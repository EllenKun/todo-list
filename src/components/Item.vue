<template>
    <li>
        <label> 
            <input type="checkbox" :checked="todo.completed" @click="handleCheck(todo.id)">
            <!-- 可实现动态绑定，但修改了props传递的值，不推荐使用 -->
            <!-- <input type="checkbox" v-model="todo.completed"> -->
            <span>{{todo.title}}</span>
        </label>
        <button class="btn btn-delete" @click="deleteTodo(todo.id)">删除</button>
    </li>
</template>

<script>
export default {
    name:'Item',
    props:['todo','changeCompleted','deleteItem'],
    methods:{
        handleCheck(id){
            this.changeCompleted(id)
        },
        deleteTodo(id){
            if(confirm('确认删除吗？')){
                this.deleteItem(id)
                // console.log("id",id)
            }
        }
    }


}
</script>
    
<style scoped>
    li{
        list-style: none;
        height: 36px;
        line-height: 36px;
        padding: 0 5px;
        border-bottom: 1px solid #ddd;
    }
    li label{
        float:left;
        cursor: pointer;
    }

    li label li input{
        vertical-align: middle;
        margin-right: 6px;
        position: relative;
        top: -1px;
    }

    li button{
        float: right;
        display: none;
        margin-top: 3px;
    }

    li:before{
        content: initial;
    }
    li:last-child{
        border-bottom: none;
    }
    li:hover{
        background-color: #ddd;
    }
    li:hover button{
        display: block;
    }

</style>