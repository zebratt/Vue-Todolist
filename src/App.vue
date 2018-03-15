<template>
    <div id="App">
        <div class="header">
            <input type="text" v-model="newItem" @keyup.enter='newItemEnter'>
            <button @click="addNewItem">Add new item</button>
        </div>
        <div class="items" :key="index" v-for="(item, index) in items" @click='clickItem(item)' :class='{completed:item.iscompleted}'>
            {{item.item}}
        </div>
        <div>
            <h1>Tests</h1>
            <Test></Test>
        </div>
    </div>
</template>
<script>
import Test from './modules/Test.vue'

export default {
    name: 'app',
    data: () => ({
        items: [],
        newItem: ''
    }),
    methods: {
        clickItem(item) {
            item.iscompleted = !item.iscompleted
        },
        newItemEnter() {
            this.addNewItem()
        },
        addNewItem() {
            if (this.newItem) {
                this.items.push({ item: this.newItem, iscompleted: false })
                this.newItem = ''
            }
        }
    },
    components: {
        Test
    }
}
</script>
<style lang="scss" scoped>
@import './App.scss';
</style>
