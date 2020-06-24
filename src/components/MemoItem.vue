<template>
    <div :class="'wrapper-item '+(item.status === 3 ? 'status3' : '')">
        <div class="check" @click="onUpdate" :data="item.status">
            <span v-html="getClassName"></span>
        </div>
        <div class="memo-content">{{ item.content }}</div>
        <div @click="deleteMemo(item.id)" class="trash">
            <i class="fas fa-trash-alt"></i>
        </div>
    </div>
</template>

<script>
export default {
    name: "memo-item",
    data() {
        return {};
    },
    props: {
        item: Object,
        deleteMemo: Function,
        updateMemo: Function,
    },
    methods: {
        onUpdate() {
            this.item.status = this.item.status === 1 ? 2 : 1;
            this.updateMemo(this.item);
            console.log(this.item.status);
        },
    },
    computed: {
        getClassName() {
            console.log('run');
            
            return this.item.status === 1 ? '<i class="far fa-check-circle"></i>' : '<i class="fas fa-check-circle"></i>';
            
        }
    }
};
</script>

<style>
.wrapper-item {
    cursor: pointer;
    height: 40px;
    line-height: 40px;
    border: 1px solid #ccc;
    border-bottom: 0;
    display: flex;
    align-items: center;
}
.wrapper-item:last-child {
    border: 1px solid #ccc;
}
.wrapper-item .check {
    width: 40px;
}
.wrapper-item .memo-content {
    flex: 1;
}
.wrapper-item .trash {
    width: 60px;
    border: 1px solid #ccc;
    border-right: 0;
    box-sizing: border-box;
}
.status3{
    position: relative;
}
.status3::before{
    content: "";
    width: 100%;
    height: 1px;
    position: absolute;
    background: #ccc;
}
</style>
