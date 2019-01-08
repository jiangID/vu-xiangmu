<template>
    <footer>
        {{message.copyright}}
    </footer>
</template>
<script>
    export default {
        name: 'foot',
        //父亲组件index.vue 传到Top.vue
        props:{
            message:Object
        }
    }

</script>

<style scoped>
    footer{
        margin-top:30px;
        background: #000;
        line-height: 30px;
        color:#fff;
        text-align:center;
        margin:0 auto;
    }
</style>