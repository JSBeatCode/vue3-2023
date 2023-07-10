<template>
    <div className="row">
      <div className="col">
        <div className="input-group mb-3">
        <input
            @change="funcOnChange"
            @keyup.enter="funcChange"
            v-model="state.todo"
            className="form-control" 
            type="text" 
        />
        <input 
            @click="funcChange"
            className="btn btn-primary" 
            type="button" 
            value="submit"/>
        </div>
    </div>
    </div>
    <!-- {{state.txt}} -->
</template>
<script>
import { reactive } from 'vue';
export default {
    name: 'InsertTodo',
    props: {
        todo: String
    },
    setup(props, {emit}){
        const state = reactive({
            todo: props.todo
        })
        // const funcChange = (e) => {
        //     const val = e.target.value;
        //     // const key = e.keyCode;
        //     emit('funcChange', val);
        // }
        // const funcKeyDown = (e) => {
        //     emit('funcKeyDown', e.keyCode);
        //     if(e.keyCode===13){
        //         state.todo = '';
        //     }
        // }
        const funcOnChange = (e) => {
            const val = e.target.value;
            state.todo = val;
        }
        const funcChange = (e) => {
            const val = state.todo;
            emit('funcSubmit', val);
            if(e.keyCode===13){
                state.todo = '';
            }
        }

        const funcJustConsole = (e) => {
            console.log("funcJustConsole", e.keyCode)
        }
        return{
            funcChange,
            funcJustConsole,
            funcOnChange,
            // funcKeyDown,
            state
        }
    },
    emits: [
        // 'funcChange',
    'funcSubmit'
    // , 'funcKeyDown'
    ]
}
</script>
<style lang="">
    
</style>