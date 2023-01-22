<script>
export default {
	props: {
		todo: Object
	},
	methods: {
		handleRemoveTodo (id) {
			this.$emit("remove", id)
		},
		handleCompletedTodo (id) {
			this.$emit("complete", id)
		},
	}
}
</script>

<template>
	<div class="todo-item">
			<div>
				<span :class="{ completed: todo.completed }"><strong>{{ todo.title }}</strong></span>
				<div :class="{ completed: todo.completed }">{{ todo.text }}</div>
			</div>
			<div>
				<button @click="handleCompletedTodo(todo.id)">{{todo.completed ? "Не выполнено" : "Выполнено"}}</button>
				<button @click="handleRemoveTodo(todo.id)">Удалить</button>
			</div>
		</div>
</template>

<style>
.todo-item {
	padding: 10px;
	border: 2px solid rgb(125, 213, 251);
	border-radius: 10px;
	margin-top: 10px;
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.completed {
	text-decoration: line-through;
	color: rgba(66, 155, 66, 0.614);
}
</style>
