<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <TodoHeader :addTodo="addTodo"/>
        <List 
          :todos="todos" 
          :changeCompleted="changeCompleted"
          :deleteItem="deleteItem"/>
        <TodoFooter :todos="todos" />
      </div>
    </div>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoFooter from './components/TodoFooter.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    TodoHeader,TodoFooter,List
  },
  data(){
    return{
        todos:[
            {id:'0001',title:'todo1',completed:true},
            {id:'0002',title:'todo2',completed:false},
            {id:'0003',title:'todo3',completed:false},
            {id:'0004',title:'todo4',completed:true},

        ]
    }
  },
  methods:{
    addTodo(todo){
      this.todos.unshift(todo)
    },
    changeCompleted(id){
      this.todos.forEach((todo) => {
        if(todo.id === id){
          todo.completed = !todo.completed
        }
      })
    },
    deleteItem(id){
      this.todos = this.todos.filter((todo) => {
        return todo.id !== id
      })
    }
  }
}
</script>

<style>
  /* base */
  body{
    background: #fff;
  }
  .btn{
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.5);
    border-radius: 4px;
  }
  .btn-delete{
    color:#fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }
  .btn-delete:hover{
    color:#fff;
    background-color: #bd362f;
  }
  .btn:focus{
    outline: none;
  }
  .todo-container{
    width:600px;
    margin:0 auto;
  }
  .todo-container .todo-wrap{
    padding:10px;
    border:1px solid #ddd;
    border-radius: 5px;
  }

</style>
