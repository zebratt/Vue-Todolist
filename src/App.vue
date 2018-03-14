<template>
    <div id="App">
        <div class="header">
            <button v-on:click="addNewItem">Add new item</button>
        </div>
        <div class="items" :key="index" v-for="(item, index) in items">
            {{item}}
        </div>
    </div>
</template>
<script>
export default {
    name: 'app',
    data: () => ({
        items: [] 
    }),
    methods: {
        addNewItem: () => {
            console.log(123);
        }
    }
}
</script>
<style lang="scss" scoped>
@import './App.scss';
</style>
