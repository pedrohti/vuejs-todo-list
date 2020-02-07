<template>
	<div class="container">
		<FormAddTask v-on:add-task="addTask"/>
		<div v-for="(t, i) in tasks" v-bind:key="i" class="row" :class="{removido: t.done}">
			<div class="col col-11 label" v-on:click="checkDone(t)">
				{{t.name}}
			</div>
			<div class="col trash">
				<em href="#" v-on:click.prevent="removeTask(i)" title="Excluir" class="fas fa-trash" />
			</div>
		</div>
		<!-- <ul v-for="(t, i) in tasks" v-bind:key="i" class="list-group">
			<li :class="{removido: t.done}" class="list-group-item d-flex justify-content-between align-items-center" v-on:click="checkDone(t)">{{t.name}}<i href="#" v-on:click.prevent="removeTask(i)" title="Excluir" class="fa fa-trash"></i></li>
		</ul> -->
	</div>
</template>

<script>
import FormAddTask from './FormAddTask'


export default {
	components: {
		FormAddTask
	},
	data() {
		return {
			tasks: []
		}
	},
	methods: {
		addTask(t) {
			this.tasks.push(t)
		},
		removeTask(i) {
			this.tasks.splice(i, 1)
		},
		checkDone(t) {
			t.done = !t.done
		}
	}
}
</script>

<style>
	ul li {
		list-style-type: none;
	}

	.removido {
		color: gray;
		text-decoration: line-through;
		background-color: rgb(0,128,0, 0.1);
	}

	em {
		color: red;
	}

	/* .col {
		border: 1px red solid;
	} */

	.label {
		text-align: left;
	}

	.trash {
		text-align: right;
	}
</style>