<template>
  <div className="container">
    <HelloWorld 
      msg="TodoList"
    />
    <InsertTodo 
      @funcSubmit="funcSubmit"
      :todo="state.todo"
    />
    <ListTodo 
      :todoList=state.todoList
      @funcDel="funcDel"
    />
  </div>
</template>

<script>
import { onMounted, onUpdated, reactive } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
import InsertTodo from './components/InsertTodo';
import { v4 as uuidv4 } from 'uuid';
import ListTodo from './components/ListTodo';

export default {
  name: 'App',
  components: {
    HelloWorld,
    InsertTodo,
    ListTodo
  },
  setup(){
    const state = reactive({
      todoList : [],
    });
    
    const funcSubmit = (val) => {
      state.todoList = [
        ...state.todoList,
        {id:uuidv4(), content:val}
      ];
    }

    const funcKeyDown = () => {
      funcSubmit();
    }

    const funcDel = (id) => {
      state.todoList = state.todoList.filter(todo => id!==todo.id);
    }

    onUpdated(()=>{
      // console.log("state의 변화가 있을 때마다 updated", state)
    })

    onMounted(()=>{
      // console.log("페이지 새로 시작할때마다 mounted", state)
    })

    return {
      state,
      // funcChange,
      funcSubmit,
      funcKeyDown,
      funcDel,
      onMounted,
      onUpdated
    }
  }
}
</script>

<style>

</style>
