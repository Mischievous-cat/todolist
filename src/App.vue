<template>
    <div id="root">
      <div class="todo-container">
        <div class="todo-wrap">
          <UserHeader :addTodo="addTodo" />
          <UserList :todos="todos" :deleteTodo="deleteTodo" />
          <UserFooter :clearAllTodo="clearAllTodo" :todos="todos" :checkAllTodo="checkAllTodo" />
        </div>
      </div>
    </div>
</template>
  
<script>
  import UserHeader from './components/UserHeader'
  import UserList from './components/UserList'
  import UserFooter from './components/UserFooter'

  export default {
      name:'App',
      components:{ UserHeader, UserList, UserFooter },
      data(){
        return {
          todos:[
            {id:'0001',title:'吃饭',completed:true},
            {id:'0002',title:'睡觉',completed:false},
            {id:'0003',title:'敲代码',completed:true},
          ]
        }
      },

    methods:{
      // 添加一个todo
      addTodo(todoObj){
        this.todos.unshift(todoObj)
      },
      
      deleteTodo(id){
        this.todos = this.todos.filter(todo=>todo.id !== id)
      },


      // 全选or全不选
      checkAllTodo(completed){
        this.todos.forEach((todo)=>{
          todo.completed = completed
        })
      },

      // 清除已完成任务
      clearAllTodo(){
        this.todos = this.todos.filter((todo)=>{
          return !todo.completed
        })
      }
    }
  }
</script>
  
<style>
  /*base*/
  body {
    background: #fff;
  }

  .btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }

  .btn-danger {
    display: none;
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }

  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }

  .btn:focus {
    outline: none;
  }

  .todo-container {
    width: 600px;
    margin: 0 auto;
  }
  .todo-container .todo-wrap {
    background-color:thistle;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }







</style>