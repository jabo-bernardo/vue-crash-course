<template>
    <div id="app">
        <AddTodo @add-todo="addTodo"/>
        <Todos :todos="todos" @del-todo="deleteTodo"/>
    </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from '../components/AddTodo';

export default {
    name: "Home",
    components: {
        Todos,
        AddTodo
    },
    data() {
        return {
            todos: []
        };
    },
    created() {
        fetch("https://jsonplaceholder.typicode.com/todos?_limit=5")
            .then(res => res.json())
            .then(res => {
                this.todos = res;
            })
            .catch(err => console.error(err));
    },
    methods: {
        deleteTodo(id) {
            this.todos = this.todos.filter(v => v.id !== id);
        },
        addTodo(todo) {
            const { title, completed } = todo;
            fetch("https://jsonplaceholder.typicode.com/todos", {
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({
                    title: title,
                    completed: completed
                })
            })
            .then(res => res.json())
            .then(res => this.todos.push(res));
        }
    }
};
</script>

<style>
* {
    margin: 0px;
    padding: 0px;
    box-sizing: border-box;
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4rem;
}
</style>
