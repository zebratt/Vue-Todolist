<template>
    <div id="Test">
        <h2>计算属性</h2>
        <input type="text" v-model="text">
        <p>text length: {{textLen}}</p>
    </div>
</template>
<script>
export default {
    data: () => ({
        text: ''
    }),
    methods: {
        showTexts(){
            console.log('text:' + this.text)
        }
    },
    computed: {
        // 要实现这个效果，我们也可以写一个方法{{textLen()}}
        // 但是如果使用方法的话，vue就不能帮我们缓存上一次的计算结果了
        textLen(){
            return this.text.length
        }
    },
    watch: {
        text(){
            this.showTexts()
        }
    }
}
</script>

