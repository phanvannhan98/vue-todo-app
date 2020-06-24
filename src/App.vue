<template>
    <div id="app">
        <div class="wrapper-memo">
            <MemoIpText test="oke" :addNewMemo="addNewMemo" />
            <MemoList
                :listMemo="listMemo"
                :deleteMemo="deleteMemo"
                :updateMemo="updateMemo"
            />
        </div>
    </div>
</template>

<script>
import MemoIpText from "./components/MemoIpText";
import MemoList from "./components/MemoList";

export default {
    name: "App",
    components: {
        MemoIpText,
        MemoList,
    },
    data() {
        return {
            listMemo: [
                {
                    id: 1,
                    content: "Memo One",
                    status: 1,
                },
                {
                    id: 2,
                    content: "Memo Two",
                    status: 2,
                },
                {
                    id: 3,
                    content: "Memo Three",
                    status: 3,
                },
                {
                    id: 4,
                    content: "Memo Four",
                    status: 1,
                },
            ],
        };
    },
    methods: {
        addNewMemo(content) {
            let id = this.listMemo.length
                ? this.listMemo[this.listMemo.length - 1].id + 1
                : 1;
            this.listMemo = [...this.listMemo, { id, content, status: 1 }];
        },
        deleteMemo(id) {
            let el = this.listMemo.find(v => v.id === id);
            if(el && el.status === 3){
                this.listMemo = this.listMemo.filter((v) => v.id !== id);
            }else{
                el.status = 3;
                this.updateMemo(el)
            }
            
        },
        updateMemo(item) {
            console.log(item.status);

            let { listMemo } = this;
            for (let i = 0; i < listMemo.length; i++) {
                if (item.id === listMemo[i].id) {
                    listMemo[i] = item;
                }
            }
            this.listMemo = [...listMemo];
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin: 0 auto;
    margin-top: 60px;
    display: flex;
    justify-content: center;
}
</style>
