<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox">
        </label>
        <span>
            <span>已完成{{doneTotal}}</span> / 全部{{todos.length}}
        </span>
        <button class="btn-delete">清除已完成项目</button>
    </div>
</template>

<script>
// import { ids } from 'webpack'
export default {
    name:'TodoFooter',
    props:['todos'],
    computed: {
        doneTotal(){
            // array.reduce条件统计
            this.todos.reduce((pre,curr)=>{
                console.log('@',pre)
                console.log('#',curr)
            },0)
        }

    }
}
</script>

<style scoped>
    .todo-footer {
        height: 40px;
        line-height: 40px;
        padding-left: 6px;
        margin-top: 5px;
    }
    .todo-footer label{
        display: inline-block;
        margin-right: 20px;
        cursor: pointer;
    }
    .todo-footer label input{
        position: relative;
        top: 1px;
        vertical-align: middle;
        margin-right: 5px;
    }

    .todo-footer button{
        float: right;
        margin-top: 5px;
    }


</style>