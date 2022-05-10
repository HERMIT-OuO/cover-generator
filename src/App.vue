<template>
    <div class="app container mx-auto flex flex-col items-center mt-8vh">
        <h1 class="text-4xl font-bold antialiased">Make your cover here.</h1>
        <Card class="mt-8" />
        <div class="mt-8 text-sm text-gray-500/80">
            @Made by
            <a href="https://hermit.world" target="_blank">HERMITOUO</a>
        </div>
    </div>
</template>

<script lang='ts'>
import { reactive, toRefs, onBeforeMount, onMounted } from "vue";
import Card from "./components/Card.vue";
interface DataProps {}
export default {
    name: "",
    components: {
        Card,
    },
    setup() {
        const data: DataProps = reactive({});
        onBeforeMount(() => {});
        onMounted(() => {});
        const refData = toRefs(data);
        return {
            ...refData,
        };
    },
};
</script>

<style>
* {
    margin: 0;
    padding: 0;

    box-sizing: border-box;
    text-decoration: none;

    font-family: "Helvetica Neue", Helvetica, Arial, "PingFang SC",
        "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei",
        sans-serif;
}

body {
    background-color: #f3f4f6;
}
</style>

<style scoped>
.app {
    width: 100%;
}
</style>