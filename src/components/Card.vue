
<template>
    <div class="card p-8 rounded-2xl">
        <div class="flex flex-row">
            <div class="relative basis-1/2 pr-4">
                <h2 class="text-2xl font-medium">Settings</h2>
                <div class="mt-4">
                    <label class="block font-medium"> Title </label>
                    <input
                        class="block border border-gray-300 p-2 w-full"
                        type="text"
                        placeholder="Enter your title here"
                        v-model="card.title"
                    />
                </div>
                <div class="mt-4">
                    <label class="block font-medium"> Author </label>
                    <input
                        class="block border border-gray-300 p-2 w-full"
                        type="text"
                        placeholder="Enter your name here"
                        v-model="card.author"
                    />
                </div>
                <div class="mt-4 flex flex-row">
                    <div class="mr-2 basis-1/2">
                        <label class="block font-medium"> Font </label>
                        <select
                            class="block border border-gray-300 p-2 w-full"
                            name="font"
                            id="cardFont"
                            v-model="card.font"
                        >
                            <option value="sans">Sans</option>
                            <option value="serif">Serif</option>
                            <option value="mono">Mono</option>
                        </select>
                    </div>
                    <div class="ml-2 basis-1/2">
                        <label class="block font-medium"> Style </label>
                        <select
                            class="block border border-gray-300 p-2 w-full"
                            name="style"
                            id="cardStyle"
                            v-model="card.style"
                        >
                            <option value="basic">Basic</option>
                            <option value="modren">Modren</option>
                            <option value="outline">Outline</option>
                            <option value="preview">Preview</option>
                        </select>
                    </div>
                </div>
                <div class="mt-4 flex flex-row">
                    <div class="mr-2 basis-1/2">
                        <label class="block font-medium"> Color </label>
                        <select
                            class="block border border-gray-300 p-2 w-full"
                            name="style"
                            id="cardStyle"
                            v-model="card.color"
                        >
                            <option v-for="(item,index) in colors" :key="index" :value="item.hex">{{ item.name }}</option>
                        </select>
                    </div>
                    <div class="ml-2 basis-1/2">
                        <label class="block font-medium"> Padding </label>
                        <select
                            class="block border border-gray-300 p-2 w-full"
                            name="style"
                            id="cardStyle"
                            v-model="card.padding"
                        >
                            <option v-for="(item, index) in paddings" :key="index" :value="item.value">{{ item.name }}</option>
                        </select>
                    </div>
                </div>
                <div class="mt-6">
                    <button
                        class="
                            border
                            bg-blue-500
                            w-full
                            h-10
                            text-white
                            font-bold
                        "
                        @click="getImg()"
                    >
                        Download
                    </button>
                </div>
                <div class="absolute bottom-0 text-sm text-center text-gray-500/80">@Made by HERMITOUO</div>
            </div>
            <div class="basis-1/2">
                <h2 class="text-2xl font-medium">Preview</h2>
                <div class="img-container mt-4 border-3 border-dashed">
                    <div
                        :class="'w-full h-full p-12' + ' ' + card.padding"
                        ref="cardRef"
                        id="realCard"
                        :style="{backgroundColor: card.color}"
                    >
                        <div
                            class="
                                real-card-inside
                                w-full
                                h-full
                                flex flex-col justify-center
                                p-4
                            "
                        >
                            <div
                                :class="
                                    classes[card.style].title +
                                    ' ' +
                                    fonts[card.font]
                                "
                            >
                                {{ card.title }}
                            </div>
                            <div
                                :class="
                                    classes[card.style].author +
                                    ' ' +
                                    fonts[card.font]
                                "
                            >
                                {{ card.author }}
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang='ts'>
import { reactive, toRefs, onBeforeMount, onMounted } from "vue";
import html2canvas from "html2canvas";
interface DataProps {
    card: {
        title: string;
        author: string;
        font: string;
        style: string;
        padding: string;
    };
    classes: {
        basic: {};
    };
    fonts: {
        sans: string;
        serif: string;
        mono: string;
    };
    cardRef: any;
    colors: any;
    paddings: any;
}
export default {
    name: "Card",
    setup() {
        const data: DataProps = reactive({
            card: {
                title: "This is a simple title",
                author: "Author",
                font: "sans",
                style: "basic",
                color: "#f3f4f6",
                padding: ""
            },
            classes: {
                basic: {
                    title: "basic_title",
                    author: "basic_author",
                },
                modren: {
                    title: "modren_title",
                    author: "modren_author",
                },
                outline: {
                    title: "outline_title",
                    author: "outline_author",
                },
                preview: {}
            },
            fonts: {
                sans: "font-sans",
                serif: "font-serif",
                mono: "font-mono",
            },
            cardRef: {},
            colors: [
                {
                    name: 'None',
                    hex: 'rgba(0, 0, 0, 0)'
                },
                {
                    name: 'Basic',
                    hex: '#f3f4f6'
                },
                {
                    name: 'Momo',
                    hex: '#f596aa'
                },
                {
                    name: 'Kuwazome',
                    hex: '#64363c'
                },
                {
                    name: 'Kuchiba',
                    hex: '#e2943b'
                },
                {
                    name: 'Uguisu',
                    hex: '#6c6a2d'
                },
                {
                    name: 'Baikocha',
                    hex: '#89916b'
                }
            ],
            paddings: [
                {
                    name: 'None',
                    value: '',
                },
                {
                    name: 'Graph Paper',
                    value: 'graph-paper',
                },
                {
                    name: 'Jig Saw',
                    value: 'jigSaw',
                },
                {
                    name: 'Hideout',
                    value: 'hideout',
                },
                {
                    name: 'Dots',
                    value: 'dots',
                },
                {
                    name: 'Falling Triangles',
                    value: 'falling-triangles',
                },
                {
                    name: 'Circuit Board',
                    value: 'circuit-board',
                },
                {
                    name: 'Temple',
                    value: 'temple',
                },
                {
                    name: 'Anchors',
                    value: 'anchors',
                },
                {
                    name: 'Brickwall',
                    value: 'brickwall',
                },
                {
                    name: 'Overlapping Circles',
                    value: 'overlapping-circles',
                },
                {
                    name: 'Wiggle',
                    value: 'wiggle',
                },
                {
                    name: 'Tic Tac Toe',
                    value: 'tic-tac-toe',
                },
                {
                    name: 'Leaf',
                    value: 'leaf',
                },
                {
                    name: 'Bubbles',
                    value: 'bubbles',
                },
                {
                    name: 'Squares',
                    value: 'squares',
                },
                {
                    name: 'Explorer',
                    value: 'explorer',
                },
                {
                    name: 'Jupiter',
                    value: 'jupiter',
                },
                {
                    name: 'Sun',
                    value: 'sun',
                },
            ]
        });
        onBeforeMount(() => {});
        onMounted(() => {});
        const refData = toRefs(data);

        const getImg = () => {
            html2canvas(data.cardRef, {
                scale: 4,
                useCORS: true,
            }).then(function (canvas) {
                let imgUrl = canvas.toDataURL("image/png");
                let tmpLink = document.createElement(
                    "a"
                ) as HTMLAnchorElement | null;
                tmpLink.style.display = "none";
                tmpLink.href = imgUrl;
                tmpLink.download = "card.png";
                tmpLink.click();
                document.body.appendChild(tmpLink);
                document.body.removeChild(tmpLink);
            });
        };

        return {
            ...refData,
            getImg,
        };
    },
};
</script>

<style scoped src="../styles/padding.css"></style>

<style scoped>
.card {
    display: block;

    width: 1200px;
    height: auto;

    background-color: white;
}

.img-container {
    width: 800px;
    height: 450px;

    border-color: #f3f4f6;
}

.real-card {
    background-color: #f3f4f6;
}

.real-card-inside {
    background-color: white;
}

.basic_title {
    margin-bottom: 2rem;

    font-size: 2.5rem;
    font-weight: 800;
    text-align: center;
}

.basic_author {
    font-size: 1.5rem;
    font-weight: 600;
    text-align: center;
}
</style>

