<template>
    <div class="todo-item" :class="{ 'is-complete': todo.completed }">
        <p>
            <input type="checkbox" @change="markComplete"> 
            {{ todo.title }}
            <button class="del" @click="$emit('del-todo', todo.id)">x</button>    
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
.todo-item {
    padding: 10px;
    border-bottom: 1px dotted #CCC;
    position: relative;
}

.is-complete {
    text-decoration: line-through;
}

.del {
    display: inline-block;
    width: 1rem;
    height: 1rem;
    line-height: 0rem;
    background-color: rgb(223, 56, 56);
    border: none;
    color: white;
    border-radius: 2px;
    position: absolute;
    outline: none;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
    cursor: pointer;
    right: 1rem;
    transition: 250ms;
}

.del:active {
    transform: scale(0.8);
}
</style>