<template>
    <div id="Test">
        <h2>计算属性</h2>
        <input type="text" v-model="text">
        <p>text length: {{textLen}}</p>
        <h2>Class和style的绑定</h2>
        <button @click="classToggle" :class="{active: isActive}">{{isActive ? 'remove class' : 'add class'}}</button>
        <div :style="{width: '100px', height: '100px', border: '#333 solid 1px', margin: '10px'}"></div>
        <h2>条件渲染</h2>
        <button @click="isOk = !isOk">change status</button>
        <span v-if="isOk">I'm ok</span>
        <span v-else>I'm not ok</span>
        <span v-show="isOk">v-show ok</span>
        <h2>列表渲染</h2>
        <span :key="item" v-for="item in items">{{item + ' '}}</span>
        <h3>v-for-object</h3>
        <span :key="key" v-for="(value, key) in person">{{key}}:{{value + '; '}}</span>
        <h2>对象的检测和变更</h2>
        <button @click="updatePerson">update person</button>
    </div>
</template>
<script>
export default {
    data: () => ({
        text: '',
        isActive: false,
        isOk: false,
        items: [
            'aaa',
            'bbb'
        ],
        person: {
            name: 'callie',
            age: 18,
            sex: 'female'
        }
    }),
    methods: {
        showTexts() {
            console.log('text:' + this.text)
        },
        classToggle(){
            this.isActive = !this.isActive
        },
        updatePerson(){
            
        }
    },
    computed: {
        // 要实现这个效果，我们也可以写一个方法{{textLen()}}
        // 但是如果使用方法的话，vue就不能帮我们缓存上一次的计算结果了
        textLen() {
            return this.text.length
        }
    },
    watch: {
        text() {
            this.showTexts()
        }
    }
}
</script>
<style lang="scss" scoped>
.active{
    background: #ff2222;
    color: #fff;
}
</style>


