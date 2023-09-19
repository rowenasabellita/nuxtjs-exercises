<template>
    <div class="mt-[4vh] flex items-center justify-center">
        <ul class="w-2/5">
            <li class="text-center border-b-2 border-black" v-for="todo in todos">
                <div class="grid grid-cols-5 text-center items-center">
                    <button @click="selectTodo(todo.id)" class="flex-no-shrink items-center text-center p-1 text-sm rounded text-black hover:text-blue-500 hover:bg-red">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M16.862 4.487l1.687-1.688a1.875 1.875 0 112.652 2.652L6.832 19.82a4.5 4.5 0 01-1.897 1.13l-2.685.8.8-2.685a4.5 4.5 0 011.13-1.897L16.863 4.487zm0 0L19.5 7.125" />
                        </svg>
                    </button>
                    <p class="col-span-3 text-center justify-center">{{ todo.title }}</p>
                    <button class="flex justify-end p-1 text-sm rounded text-black hover:text-red-500 hover:bg-red">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0" />
                        </svg>
                    </button>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        todos: Array,
    },
    data: function () {
        return {
            // todos: [],
            todoId: "",
        };
    },
    mounted: async function () {
        // const postTodo = await fetch('http://localhost:8080/todo')
        // const todoList = await postTodo.json()
        // this.todos = todoList
        console.log(this.todos);
    },
    methods: {
    }
    // methods: {
    //     selectTodo: function(todoId){
    //         this.todoId = todoId;
    //     },
        // updateTodo: function() {
            
        // },

    // },


};
</script>