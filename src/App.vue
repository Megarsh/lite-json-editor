<script setup>
    import { ref } from 'vue'
    import LiteJsonEditor from './components/LiteJsonEditor.vue'

    const defaultEditor = ref([
        {
            "_id": "635664db13b91c1c306f91a5",
            "index": 0,
            "guid": "a09ca50d-5c3c-4b00-9a3c-29f71cefa7c2",
            "isActive": true,
            "balance": "$1,029.34",
            "picture": "http://placehold.it/32x32",
            "age": 30,
            "eyeColor": "brown",
            "name": "Maynard Burke",
            "gender": "male",
            "company": "EXOSTREAM",
            "email": "maynardburke@exostream.com",
            "phone": "+1 (986) 512-2093",
            "address": "133 Ferry Place, Noxen, Wyoming, 3591",
            "about": "Labore incididunt fugiat reprehenderit reprehenderit exercitation est. Aute eiusmod et elit commodo eu ad. Ipsum cupidatat qui velit in eu voluptate adipisicing incididunt nulla officia anim magna veniam.\r\n",
            "registered": "2015-12-11T08:01:53 -04:00",
            "latitude": -31.065655,
            "longitude": -134.241803,
            "tags": [
                "ad",
                "reprehenderit",
                "in",
                "et",
                "deserunt",
                "deserunt",
                "pariatur"
            ],
            "friends": [
                {
                    "id": 0,
                    "name": "Perry Pruitt"
                },
                {
                    "id": 1,
                    "name": "Christine Griffin"
                },
                {
                    "id": 2,
                    "name": "Ruiz Hutchinson"
                }
            ],
            "greeting": "Hello, Maynard Burke! You have 3 unread messages.",
            "favoriteFruit": "banana"
        },
        {
            "_id": "635664db194aa9b56c9cd918",
            "index": 1,
            "guid": "dfc23755-2364-40de-8ce2-69ab2c603032",
            "isActive": false,
            "balance": "$1,001.38",
            "picture": "http://placehold.it/32x32",
            "age": 36,
            "eyeColor": "blue",
            "name": "Roseann Bryan",
            "gender": "female",
            "company": "KYAGORO",
            "email": "roseannbryan@kyagoro.com",
            "phone": "+1 (843) 431-3289",
            "address": "955 Banner Avenue, Southmont, Nebraska, 6351",
            "about": "Excepteur exercitation ad cupidatat consequat enim laboris exercitation esse. Laborum sint fugiat deserunt esse magna dolore adipisicing veniam. Culpa dolore consectetur reprehenderit elit cupidatat ut aliqua cupidatat laboris aliquip culpa dolor. Minim laboris proident culpa cupidatat incididunt.\r\n",
            "registered": "2016-04-02T05:23:49 -04:00",
            "latitude": -26.762275,
            "longitude": 117.303506,
            "tags": [
                "irure",
                "velit",
                "veniam",
                "eu",
                "sit",
                "dolore",
                "culpa"
            ],
            "friends": [
                {
                    "id": 0,
                    "name": "Elsie Britt"
                },
                {
                    "id": 1,
                    "name": "Lilly Erickson"
                },
                {
                    "id": 2,
                    "name": "Annie Dominguez"
                }
            ],
            "greeting": "Hello, Roseann Bryan! You have 1 unread messages.",
            "favoriteFruit": "strawberry"
        },
        {
            "_id": "635664db9e9dc590aa51f732",
            "index": 2,
            "guid": "8246ba9b-4ab2-45d3-9e64-522eb57c1bfd",
            "isActive": true,
            "balance": "$2,338.10",
            "picture": "http://placehold.it/32x32",
            "age": 24,
            "eyeColor": "green",
            "name": "Becky Banks",
            "gender": "female",
            "company": "SPHERIX",
            "email": "beckybanks@spherix.com",
            "phone": "+1 (916) 400-3279",
            "address": "797 Nevins Street, Inkerman, Utah, 6823",
            "about": "Est amet ullamco est nisi deserunt. Eu cillum exercitation ipsum officia. Commodo ex et dolor officia est cillum exercitation sint amet minim. Qui eiusmod nisi anim reprehenderit exercitation laborum deserunt veniam quis. Proident adipisicing exercitation ut et sint consequat commodo cupidatat amet labore fugiat. Minim exercitation cupidatat occaecat aliquip incididunt eu velit et ad irure elit nisi pariatur.\r\n",
            "registered": "2018-07-22T06:02:47 -04:00",
            "latitude": 84.008326,
            "longitude": 72.222565,
            "tags": [
                "cupidatat",
                "consectetur",
                "officia",
                "ea",
                "commodo",
                "adipisicing",
                "velit"
            ],
            "friends": [
                {
                    "id": 0,
                    "name": "Lilia Whitney"
                },
                {
                    "id": 1,
                    "name": "Barrett Grimes"
                },
                {
                    "id": 2,
                    "name": "Velasquez Downs"
                }
            ],
            "greeting": "Hello, Becky Banks! You have 4 unread messages.",
            "favoriteFruit": "banana"
        },
        {
            "_id": "635664db38119f7eecc2edb9",
            "index": 3,
            "guid": "c2d136af-3d35-45cc-9bca-701de51effee",
            "isActive": true,
            "balance": "$2,958.42",
            "picture": "http://placehold.it/32x32",
            "age": 34,
            "eyeColor": "brown",
            "name": "Fitzgerald Boyle",
            "gender": "male",
            "company": "MOBILDATA",
            "email": "fitzgeraldboyle@mobildata.com",
            "phone": "+1 (834) 440-2280",
            "address": "769 Village Road, Cliffside, Wisconsin, 1365",
            "about": "Occaecat commodo eu duis in ea quis. Ea sunt duis ea mollit exercitation minim commodo mollit ea. Nostrud qui velit non et reprehenderit consectetur officia et consequat elit esse. Et tempor commodo exercitation magna consectetur incididunt laboris in reprehenderit cupidatat est non Lorem cupidatat. Est labore amet ex culpa ex. Veniam laboris enim cupidatat minim culpa sint quis excepteur elit deserunt id sit duis ut.\r\n",
            "registered": "2022-08-11T02:12:27 -04:00",
            "latitude": 82.962635,
            "longitude": 38.513156,
            "tags": [
                "esse",
                "sint",
                "do",
                "duis",
                "non",
                "exercitation",
                "esse"
            ],
            "friends": [
                {
                    "id": 0,
                    "name": "Harper Mcknight"
                },
                {
                    "id": 1,
                    "name": "Crane Avery"
                },
                {
                    "id": 2,
                    "name": "Roberta Harper"
                }
            ],
            "greeting": "Hello, Fitzgerald Boyle! You have 7 unread messages.",
            "favoriteFruit": "strawberry"
        },
        {
            "_id": "635664dbddda7a07b1f88f1c",
            "index": 4,
            "guid": "c311e78d-ad9a-4823-a39c-4dc84eef9d61",
            "isActive": true,
            "balance": "$2,287.24",
            "picture": "http://placehold.it/32x32",
            "age": 32,
            "eyeColor": "blue",
            "name": "Cohen Wise",
            "gender": "male",
            "company": "POLARIA",
            "email": "cohenwise@polaria.com",
            "phone": "+1 (936) 412-2483",
            "address": "453 Jefferson Avenue, Avalon, Georgia, 3593",
            "about": "Culpa tempor tempor culpa ea. Velit enim consequat minim labore Lorem duis sunt ut. Aliqua cupidatat exercitation aute aliqua laboris sit ullamco. Duis Lorem velit commodo aliquip labore cupidatat voluptate occaecat. Eiusmod id velit sint officia duis. Consectetur ad laboris minim occaecat ipsum adipisicing excepteur sint ut eu. Officia cillum tempor cillum tempor nisi sit fugiat deserunt.\r\n",
            "registered": "2015-08-01T04:43:38 -04:00",
            "latitude": 67.450364,
            "longitude": -26.526592,
            "tags": [
                "sunt",
                "irure",
                "nulla",
                "eiusmod",
                "eu",
                "est",
                "nostrud"
            ],
            "friends": [
                {
                    "id": 0,
                    "name": "Dora Jennings"
                },
                {
                    "id": 1,
                    "name": "Short Jackson"
                },
                {
                    "id": 2,
                    "name": "Blake Hicks"
                }
            ],
            "greeting": "Hello, Cohen Wise! You have 1 unread messages.",
            "favoriteFruit": "banana"
        }
    ])

    const indent = ref(3)
    const withoutError = ref(true)
    const withoutEdit = ref(true)
</script>

<template>
    <div class="parent">
        <div class="left">
            <h2>Lite Json Editor</h2>

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
            <h3>Default</h3>
            <LiteJsonEditor class="editor" v-model="defaultEditor" :indent="indent" :withoutError="!withoutError" :withoutEdit="!withoutEdit" />
            <h3>Dark</h3>
            <LiteJsonEditor class="editor" v-model="defaultEditor" dark :indent="indent" :withoutError="!withoutError" :withoutEdit="!withoutEdit" />
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
        max-width: 800px;
        height: 400px;
        border-radius: 6px;
        border: 1px solid #bcbcbc;
        margin-bottom: 20px;
    }
</style>
