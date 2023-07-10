<template>
  <div className="row">
    <div className="col">
        <div className="card" v-for="todo in todoList" v-bind:key="todo.id">
            <div className="card-body" 
                @click="$emit('funcDel', todo.id)"
            >
            {{todo.content}}
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'ListTodo',
    props: {
        todoList: Array
    },
    emit:['funcDel']
        
}
</script>

<style>

</style>