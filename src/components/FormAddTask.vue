<template>
	<div class="form-todo form-group">
		<h1>Lista de Tarefas</h1>
		<p>
			<input placeholder="Adicione uma tarefa" type="text" name="task" class="form-control" v-model="name">
		</p>
		<button type="submit" v-on:click="addTask" class="btn btn-primary">Adicionar</button>
		<hr />
	</div>
</template>

<script>
export default {
	data() {
		return {
			name: '',
			done: ''
		}
	},
	methods: {
		addTask() {
			if(this.name.trim() === '') { return }

			this.$emit('add-task', {
				name: this.name,
				done: false
			})

			this.name = ''
		},
	},
}
</script>