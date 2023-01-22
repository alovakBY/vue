<template>
	<CreateTodo @create="createTodo" />
	<div class="todos-container">
		<TodoItem v-if="todos.length" v-for="todo in todos" :key="todo.id" :todo="todo" @complete="completedTodo"
			@remove="removeTodo" />
		<div v-else>
			Нет задач
		</div>
	</div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue"
import CreateTodo from "./components/CreateTodo.vue"
export default {
	components: {
		TodoItem,
		CreateTodo,
	},
	data() {
		return {
			todoTitle: '',
			todoText: '',
			todos: [],
		}
	},
	methods: {
		removeTodo(id) {
			this.todos = this.todos.filter((todo) => todo.id !== id)
		},
		completedTodo(id) {
			this.todos = this.todos.map((todo) => todo.id === id ? { ...todo, completed: !todo.completed } : todo)
		},
		createTodo(todo) {
			this.todos = [todo, ...this.todos]
		},
	},
	mounted() {
		fetch("https://jsonplaceholder.typicode.com/todos").then(data => data.json()).then((todos) => this.todos = todos)
	},
}
</script>

<style scoped>
.todos-container {
	margin-top: 20px;
}
</style>
