<template>
    <div style="flex:1">
        <guarantee></guarantee>
    </div>
</template>

<!--引入bui-weex样式文件-->
<style lang="scss" src="bui-weex/src/css/buiweex.scss"></style>

<script>
    import guarantee from "./guarantee.vue";
    module.exports = {
        data () {
            return {}
        },
        components: {
          guarantee
        }
    }
</script>