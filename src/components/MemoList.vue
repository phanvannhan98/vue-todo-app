<template>
    <div class="memo-list">
        <MemoItem
            v-for="(item, index) in listMemo"
            :key="index"
            :item="item"
            :deleteMemo="deleteMemo"
            :updateMemo="updateMemo"
        />
    </div>
</template>

<script>
import MemoItem from "./MemoItem";
export default {
    name: "memo-list",
    components: {
        MemoItem,
    },
    data() {
        return {};
    },
    props: {
        listMemo: Array,
        deleteMemo: Function,
        updateMemo: Function,
    },
};
</script>

<style>
.memo-list {
    margin-top: 10px;
}
</style>
