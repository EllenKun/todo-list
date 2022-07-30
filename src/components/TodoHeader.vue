<template>
    <div class="todo-header">
        <input type="text" placeholder="请输入任务名称，点击回车确认" v-model="title" @keyup.enter="add" />
    </div>
</template>

<script>
import {nanoid} from 'nanoid'
export default {
    name:'ToDoHeader',
    data(){
        return{
            title:''
        }
    },
    props:['addTodo'],
    methods:{
        // 1.监听事件对象
        // add(event){
        //     // console.log(event.target.value)
        //     const todo = {
        //         // uuid生成唯一字符串 =>nanoid
        //         id: nanoid(),
        //         title: event.target.value,
        //         completed: false
        //     }
        //     // console.log("todo",todo)
        //     this.addTodo(todo)
        //     event.target
        // }
        //  2.双向数据绑定
        add(){
            if (!this.title.trim()){
                alert('输入不可为空！')
                return
            }
            const todo = {
                id: nanoid(),
                title: this.title,
                completed: false
            }
            this.addTodo(todo)
            this.title = ''
        }
    },

}
</script>

<style scoped>
/* header */
    .todo-header input{
        width: 560px;
        height: 28px;
        font-size: 14px;
        border: 1px solid #ccc;
        border-radius: 4px;
        padding: 4px 7px;
    }

    .todo-header input:focus{
        outline: none;
        border-color: rgba(82, 168, 236, 0.8);
        box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.01),0 0 8px rgba(82, 168, 236, 0.8);
    }
</style>