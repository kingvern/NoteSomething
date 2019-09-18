<template>
    <!-- app.vue 的template标签内只能有一个节点 -->
    <div id="app">
        <div id="wallpaper"></div>
        <div id="cover"></div>
        <APP_Header></APP_Header>
        <APP_Todo></APP_Todo>
        <APP_Footer></APP_Footer>
    </div>
</template>

<script>
    // 引入header.vue组件
    import APP_Header from './todo/header.vue';

    // 引入footer.jsx组件
    import APP_Footer from './todo/footer.jsx';

    // 引入todo.vue组件
    import APP_Todo from './todo/todo.vue';

    export default {
        // 声明组件，之后便可以使用组件标签
        components: {
            APP_Header,
            APP_Footer,
            APP_Todo
        }
    }
</script>

<!-- 设置scoped 表示当前组件下的id只在当前组件起作用，不会跟其他组件引起冲突 -->
<style lang="stylus" scoped>
    #app {
        position absolute
        left 0
        right 0
        top 0
        bottom 0
    }

    #cover {
        position fixed
        left 0
        right 0
        top 0
        bottom 0
        background-color #555
        opacity 0.2
        z-index -1
        width 100%
        height 100%
    }

    #wallpaper {
        //filter blur(2px)
        opacity 0.8
        background-image url(assets/images/Wallpaper1.jpg)
        z-index -1
        left 0
        top 0
        width 100%
        height 100%
        position fixed
        background-repeat no-repeat
        background-size cover
        background-position 50%
    }

</style>
