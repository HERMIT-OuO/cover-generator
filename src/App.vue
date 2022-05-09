<template>
    <div class="app">
      <h1>Make your cover here.</h1>
      <Card />
    </div>
</template>

<script lang='ts'>
import { reactive, toRefs, onBeforeMount, onMounted } from "vue";
import  Card  from './components/Card.vue';
interface DataProps {}
export default {
    name: "",
    components: {
      Card
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
<style scoped>
</style>