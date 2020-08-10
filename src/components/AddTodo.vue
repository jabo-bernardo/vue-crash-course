<template>
    <div class="">
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo">
            <button  class="btn" type="submit">Create Todo</button>

        </form>
    </div>
</template>

<script>
// import { v4 as uuidv4 } from 'uuid'

export default {
    name: "AddTodo",
    data() {
        return {
            title: ""
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            if(this.title.length == 0) return;
            const newTodo = {
                title: this.title,
                completed: false
            }
            this.title = "";
            this.$emit("add-todo", newTodo);
        }
    }
}
</script>

<style scoped>
    * {
        outline: none;
    }

    div {
        padding: 1rem;
    }
    form {
        display: flex;
        column-gap: 0.5rem;
    }
    input {
        flex: 10;
        padding: 5px;
        border: 1px solid #DDD;
        border-radius: 4px;
    }
    
    button {
        flex: 2;
        background-color: rgb(58, 58, 58);
        color: white;
        font-weight: bold;
        border: none;
        border-radius: 4px;
        box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
        cursor: pointer;
        font-size: 0.8rem;
        transition: 250ms;
    }

    button:active {
        transform: scale(0.95);
    }
</style>