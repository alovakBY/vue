<template >
	<div class="top">
		<h3 class="top-title">Добавить задачу</h3>
		<input class="input" type="text" placeholder="Введите заголовок" v-model="title">
		<button class="btn" @click="handleCreateTodo">Добавить задачу</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			title: "",
		}
	},
	emits: ["create"],
	methods: {
		handleCreateTodo() {
			this.$emit("create", {
				id: Date.now(),
				title: this.title,
				completed: false,
			})
			this.title = ""
		},
	}
}
</script>

<style >
.top {
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}

.input {
	width: 500px;
	margin-top: 10px;
	border: 1px solid rgb(252, 103, 103);
	padding: 5px;
}

.top-title {
	margin-bottom: 10px;
}

.btn {
	width: max-content;
	margin-top: 10px;
	background-color: rgb(252, 103, 103);
	border: none;
	padding: 10px;
	color: aliceblue;
	cursor: pointer;
}
</style>