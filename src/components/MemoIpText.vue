<template>
    <div class="wrapper-ip">
        <input
            @keyup.enter="submit"
            v-model="inputTxt"
            class="memo-text"
            type="text"
        />
        <div @click="submit" class="icon">
            <i class="fas fa-plus-circle"></i>
        </div>
    </div>
</template>

<script>
export default {
    name: "memoip-text",
    props: {
        test: String,
        addNewMemo: Function,
    },
    data() {
        return {
            inputTxt: "",
        };
    },
    methods: {
        submit() {
            this.addNewMemo(this.inputTxt);
        },
    },
};
</script>

<style>
.wrapper-ip {
    display: flex;
    height: 60px;
    width: 400px;
}
.wrapper-ip input {
    height: 100%;
    flex: 1;
    box-sizing: border-box;
    font-size: 24px;
    text-align: center;
    border: 1px solid #ccc;
    border-right: 0;
}
.wrapper-ip .icon {
    height: 100%;
    width: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #ccc;
    box-sizing: border-box;
    cursor: pointer;
}
</style>
