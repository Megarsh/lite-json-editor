<script setup>
    import { nextTick, computed } from 'vue'

    const props = defineProps({
        modelValue: {
            type: [String, Object, null],
            required: true
        },
        indent: {
            type: Number,
            default: 3
        },
        dark: Boolean,
        formatting: Object,
        withoutEdit: Boolean,
        withoutError: Boolean
    })
    const emits = defineEmits(['update:modelValue'])

    const defaultFormats = computed(() => ({
        'number': '#a9dc76',
        'braces': '#84aecc',
        'brackets': '#d26a6a',
        'colon': props.dark ? '#ffffff' : '#4f4f4f',
        'comma': props.dark ? '#ffff25' : '#f8c33b',
        'string': props.dark ? '#78dce8' : '#5f9fca',
        'string_quotes': '#e393ff',
        'key': '#ff6188',
        'key_quotes': '#fc9867',
        'null': '#cccccc',
        'true': props.dark ? '#c2e69f' : '#8ccf79',
        'false': '#e69fc2'
    }))

    const part = computed(() => props.formatting ? Object.keys(defaultFormats.value).reduce((p, c) => ({ ...p, [c]: props.formatting[c] ?? defaultFormats.value[c]}), {}) : defaultFormats.value)

    // Caret Control

    const get_caret_pointer = target => {
        const selection = document.getSelection()

        if (selection.rangeCount > 0) {
            const range = selection.getRangeAt(0)
            const caret_range = range.cloneRange()

            caret_range.selectNodeContents(target)
            caret_range.setEnd(range.endContainer, range.endOffset)

            const section = caret_range.toString()
            const character = section[section.length - 1]
            const occurrence = get_number_of_occurrences(section, character)

            return { character, occurrence, section }
        }

        return null
    }

    const set_caret_from_pointer = (target, pointer) => {
        const selection = window.getSelection()
        const range = document.createRange()
        let nodes_to_explore = get_text_nodes(target)
        let occurrence = pointer.occurrence
        let fount_at = 0, node

        for (let i = 0; i < nodes_to_explore.length; i++) {
            node = nodes_to_explore[i]

            fount_at = get_position_of_occurrence(node.textContent, pointer.character, occurrence)

            if (fount_at >= 0)
                break

            occurrence -= get_number_of_occurrences(node.textContent, pointer.character)
        }

        fount_at++
        range.setStart(node, fount_at)
        range.setEnd(node, fount_at)
        selection.removeAllRanges()
        selection.addRange(range)
    }

    // Utils

    const escape_regex_string = string => string.replace(/[.*+?^${}()|[\]\\]/g, '\\$&')

    const get_position_of_occurrence = (string, sub_string, occurrence) => {
        const position = string.split(sub_string, occurrence).join(sub_string).length

        return position === string.length ? -1 : position
    }

    const get_number_of_occurrences = (string, sub_string) => sub_string ? string.replace(new RegExp(`[^${escape_regex_string(sub_string)}]`, 'g'), '').length : 0

    const get_text_nodes = element => {
        let node, list = [], walk = document.createTreeWalker(element, NodeFilter.SHOW_TEXT, null, false)

        while (node = walk.nextNode())
            list.push(node)

        return list
    }

    // Formatting

    const format_object = (input, offset = 0) => {
        if (input === null)
            return `<span style="color: ${part.value.null}">null</span>`

        let output = ''

        output += `<span style="color: ${part.value.braces}">{</span>\n`

        Object.keys(input).forEach((key, index, list) => output += `${'&nbsp;'.repeat(offset + props.indent)}<span style="color: ${part.value.key}"><span style="color: ${part.value.key_quotes}">"</span>${key}<span style="color: ${part.value.key_quotes}">"</span></span><span style="color: ${part.value.colon}">:</span>${format_input(input[key], offset + props.indent)}${index < list.length - 1 ? `<span style="color: ${part.value.comma}">,</span>` : ''}\n`)

        output += '&nbsp;'.repeat(offset)
        output += `<span style="color: ${part.value.braces}">}</span>`

        return output
    }

    const format_array = (input, offset = 0) => {
        let output = ''

        output += `<span style="color: ${part.value.brackets}">[</span>\n`

        input.forEach((value, index, list) => output += `${'&nbsp;'.repeat(offset + props.indent)}<span>${format_input(value, offset + props.indent)}</span>${index < list.length - 1 ? `<span style="color: ${part.value.comma}">,</span>` : ''}\n`)

        output += '&nbsp;'.repeat(offset)
        output += `<span style="color: ${part.value.brackets}">]</span>`

        return output
    }

    const format_string = input => `<span style="color: ${part.value.string}"><span style="color: ${part.value.string_quotes}">"</span>${input}<span style="color: ${part.value.string_quotes}">"</span></span>`

    const format_boolean = input => `<span style="color: ${part.value[input]}">${input}</span>`

    const format_number = input => `<span style="color: ${part.value.number}">${input}</span>`

    const format_input = (input, offset = 0) => {
        const type = Array.isArray(input) ? 'array' : typeof input

        return format_type[type] ? format_type[type](input, offset) : input
    }

    const format_type = {
        object: format_object,
        array: format_array,
        string: format_string,
        boolean: format_boolean,
        number: format_number
    }

    // Value Control

    const proxy = computed({
        get: () => props.modelValue ? format_input(typeof props.modelValue === 'string' ? JSON.parse(props.modelValue) : props.modelValue) : '',
        set: async target => {
            try {
                const formatted = target.innerText.split(/[\xa0\n]+/).join('')
                let current = formatted ? JSON.parse(formatted) : null
                let check

                if (typeof props.modelValue === 'string') {
                    current = current ? JSON.stringify(current) : ''
                    check = current !== props.modelValue
                } else check = JSON.stringify(current) !== JSON.stringify(props.modelValue)

                if (!props.withoutError)
                    target.nextElementSibling.style.display = 'none'

                if (check) {
                    const pointer = current && get_caret_pointer(target)

                    emits('update:modelValue', current)

                    if (pointer) {
                        await nextTick()

                        set_caret_from_pointer(target, pointer)
                    }
                }
            }
            catch {
                if (!props.withoutError)
                    target.nextElementSibling.style.display = 'block'
            }
        }
    })
</script>

<template>
    <div style="position: relative">
        <div :style="[dark && 'background: #252530; color: #ffffff', 'height: 100%; width: 100%; padding: 4px; border-radius: inherit; font-family: monospace; overflow: auto; outline: none; white-space: pre-wrap; box-sizing: border-box']" :contentEditable="!withoutEdit" @keyup="event => proxy = event.target" v-html="proxy" />
        <slot>
            <div v-if="!withoutError" class="error-popup" style="display: none; position: absolute; bottom: 6px; right: 24px; color: #d23b3b; font-size: 12px; font-weight: 600; user-select: none">Incorrect JSON format</div>
        </slot>
    </div>
</template>
