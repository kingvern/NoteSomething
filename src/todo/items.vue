<template>
    <div :class="['todo-item', todo.completed ? 'completed' : '', this.editing ? 'editing': 'finished']">
        <div class="view">
            <input type="checkbox"
                   class="toggle"
                   v-model="todo.completed"
            >
            <label @click="clickEdit">{{todo.content}}</label>

            <button class="destroy" @click="deleteTodo"></button>
        </div>
        <input class="input" v-model="todo.content"  @blur="clickEdit" >
    </div>

</template>

<script>
    export default {
        // 父子组件间传值
        props: {
            // 接收父组件todo.vue传过来的todo对象
            cache: {
                type: Object,
                require: true
            },
            todo: {
                type: Object,
                require: true
            }
        },
        data() {
            return {
                editing: false
            }
        },
        methods: {
            editTodo() {
                // this.$emit 触发del事件，并返回todo.id
                // 往父组件传递 del 方法
                this.$emit('edit', this.todo)

            },
            clickEdit() {
                this.editing = !this.editing
            },
            doneEdit() {

            },
            cancelEdit() {

            },
            deleteTodo() {
                // this.$emit 触发del事件，并返回todo.id
                // 往父组件传递 del 方法
                this.$emit('del', this.todo.id)

            }
        }
    }
</script>

<style lang="stylus" scoped>
    .todo-item {
        position relative
        background-color #fff
        font-size 18px
        border-bottom 1px solid rgba(0, 0, 0, 0.06)
        &:hover {
            .destroy:after {
                content: '×'
            }
        }
        label {
            white-space: pre-line;
            word-break: break-all;
            padding: 15px 60px 15px 15px;
            margin-left: 45px;
            display: block;
            line-height: 1.2;
            transition: color 0.4s;
        }
        &.completed {
            label {
                color: #d9d9d9;
                text-decoration line-through
            }
        }
        .input {
            display: none
        }

    }

    .editing .input {
        display: block
    }
    .editing label {
        display: none
    }

    .finished label{
        display: block
    }

    .finished .input{
         display: none
    }

    .input {
        white-space: pre-line;
        word-break: break-all;
        padding: 15px 60px 15px 15px;
        margin-left: 45px;
        width: 475px;
        display: block;
        line-height: 1.2;
        transition: color 0.4s;
        font-size: 18px;
        color: #333;
    }

    .toggle {
        text-align: center;
        width: 40px;
        height: 40px;
        line-height: 40px
        position: absolute;
        top: 0;
        bottom: 0;
        margin: auto 0;
        border: none;
        appearance: none;
        outline none
        padding-left 5px
        cursor pointer
        &:after {
            content: url('../assets/images/round.svg')
        }
        &:checked:after {
            content: url('../assets/images/done.svg')
        }
    }

    .destroy {
        position: absolute;
        top: 0;
        right: 10px;
        bottom: 0;
        width: 40px;
        height: 40px;
        margin: auto 0;
        font-size: 18px;
        color: #cc9a9a;
        margin-bottom: 11px;
        transition: color 0.2s ease-out;
        background-color transparent
        appearance none
        border-width 0
        cursor pointer
        outline none
    }

</style>
