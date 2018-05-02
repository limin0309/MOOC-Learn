<template>
    <div>

    </div>
</template>

<script>
    new Vue({
        el:'#app',
        data:{title:"Hello Vue"
        },
        filters:{

        },
        mounted:function () {
            this.cartView();
        },
        methods: {
            cartView:function () {
                this.title="vue hello"
            }
        },
    })
</script>

<style scoped lang="less">

</style>
