<template>
    <div id="App">
        <div class="header">
            <input type="text" v-model="newItem" @keyup.enter='newItemEnter'>
            <button v-on:click="addNewItem">Add new item</button>
        </div>
        <div class="items" :key="index" v-for="(item, index) in items" @click='clickItem(item)' :class='{completed:item.iscompleted}'>
            {{item.item}}
        </div>
    </div>
</template>
<script>
export default {
    name: 'app',
    data: () => ({
        items: [] ,
        newItem:''
    }),
    methods: {
        clickItem(item){
            //this.items[index].iscompleted = !this.items[index].iscompleted;
            item.iscompleted = !item.iscompleted;
        },
        newItemEnter(){
            this.addNewItem();
        },
        addNewItem() {
            if(this.newItem){
                this.items.push({item:this.newItem,iscompleted:false});
                this.newItem = '';
            }
        }
    }
}
</script>
<style lang="scss" scoped>
@import './App.scss';
</style>
