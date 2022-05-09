
<template>
    <div class="">
        Card
    </div>
</template>

<script lang='ts'>
import { reactive, toRefs, onBeforeMount, onMounted } from "vue";
interface DataProps {}
export default {
    name: "Card",
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