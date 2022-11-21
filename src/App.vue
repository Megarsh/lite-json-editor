<script setup>
    import { ref } from 'vue'
    import LiteJsonEditor from './components/LiteJsonEditor.vue'

    const defaultEditor = ref([{"_id":"6357fbfb59799ffbeadb6ee1","index":0,"guid":"1bb61526-4c51-4a06-9f36-5bf4961336ea","isActive":true,"balance":"$1,988.37","picture":"http://placehold.it/32x32","age":31,"eyeColor":"blue","name":"Ramsey Shields","gender":"male","company":"HYDROCOM","email":"ramseyshields@hydrocom.com","phone":"+1 (944) 486-3020","address":"387 Monitor Street, Hardyville, South Dakota, 1743","about":"Ullamco do pariatur culpa anim occaecat elit sit ea labore reprehenderit excepteur ex. Do quis labore esse aliqua eiusmod exercitation sint laborum. Nulla qui sit Lorem mollit reprehenderit dolore magna magna. Nulla ex irure non enim consectetur excepteur nisi excepteur. Sint tempor esse qui est anim dolore proident aliquip excepteur elit aliquip ut in.","registered":"2019-02-14T01:12:52 -04:00","latitude":19.873721,"longitude":63.468217,"tags":["cupidatat","irure","duis","culpa","non","do","amet"],"friends":[{"id":0,"name":"Freida Stewart"},{"id":1,"name":"Townsend Figueroa"},{"id":2,"name":"Maynard Galloway"}],"greeting":"Hello, Ramsey Shields! You have 5 unread messages.","favoriteFruit":"banana"},{"_id":"6357fbfb8c0ba345d8127ff7","index":1,"guid":"f349371a-9c16-44c9-9723-edb6f7f76377","isActive":true,"balance":"$1,963.06","picture":"http://placehold.it/32x32","age":28,"eyeColor":"green","name":"Sparks Hawkins","gender":"male","company":"CABLAM","email":"sparkshawkins@cablam.com","phone":"+1 (834) 408-3374","address":"482 Grand Street, Ripley, Marshall Islands, 6614","about":"Sint anim occaecat ut sunt. Aute est elit nostrud sunt cupidatat. Tempor occaecat esse eiusmod culpa id. Sunt et officia anim et duis consequat labore nulla nostrud excepteur dolore dolore non. Irure velit duis tempor fugiat. Mollit aliquip magna exercitation eu mollit amet id. Labore quis ipsum culpa non ut dolor.","registered":"2017-11-21T08:00:03 -04:00","latitude":19.865809,"longitude":-158.395435,"tags":["esse","esse","dolore","veniam","dolor","laboris","nisi"],"friends":[{"id":0,"name":"Bullock Hooper"},{"id":1,"name":"Erica Mckenzie"},{"id":2,"name":"Cheri Moody"}],"greeting":"Hello, Sparks Hawkins! You have 10 unread messages.","favoriteFruit":"banana"}])

    const indent = ref(3)
    const withoutError = ref(true)
    const withoutEdit = ref(true)
    const dark = ref(false)
</script>

<template>
    <div class="parent">
        <div class="left">
            <h2>Lite Json Editor</h2>

            <div class="inputs">
                <label>
                    <input type="checkbox" v-model="dark" />
                    <span>Dark Mode</span>
                </label>
            </div>
            <div class="inputs">
                <label>
                    <input type="checkbox" v-model="withoutError" />
                    <span>Show Error</span>
                </label>
            </div>
            <div class="inputs">
                <label>
                    <input type="checkbox" v-model="withoutEdit" />
                    <span>Allow Edit</span>
                </label>
            </div>
            <div class="inputs">
                <div>Indent</div>
                <input type="number" v-model="indent" />
            </div>
        </div>
        <div>
            <h3>Editor</h3>
            <LiteJsonEditor class="editor" v-model="defaultEditor" :dark="dark" :indent="indent" :withoutError="!withoutError" :withoutEdit="!withoutEdit" />
            <h3>Custom Error</h3>
            <LiteJsonEditor class="editor" v-model="defaultEditor" :indent="indent" :withoutError="!withoutError" :withoutEdit="!withoutEdit">
                <div class="error" style="display: none">
                    <svg width="100" height="100" viewBox="0 0 100 100" fill="white" xmlns="http://www.w3.org/2000/svg">
                        <path d="M3.12018 3.05139L97.0514 96.8798" stroke="white" stroke-width="8"/>
                        <path d="M3.17157 96.9312L97 3" stroke="white" stroke-width="8"/>
                    </svg>
                </div>
            </LiteJsonEditor>
        </div>
    </div>
</template>

<style scoped>
    .error {
        position: absolute;
        top: 20px;
        right: 20px;
        border-radius: 100%;
        background: #cd1c1c;
        padding: 10px;
        width: 20px;
        height: 20px;
    }
    .error svg {
        width: 100%;
        height: 100%;
    }
    .parent {
        display: flex;
        align-items: baseline;
    }
    .left {
        position: sticky;
        top: 8px;
        margin-right: 24px;
    }
    .inputs {
        margin-bottom: 10px;
    }
    .editor {
        width: 800px;
        height: 400px;
        border-radius: 6px;
        border: 1px solid #bcbcbc;
        margin-bottom: 20px;
    }
</style>
