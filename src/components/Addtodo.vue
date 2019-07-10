<template>
	<div>
		<form @submit="addTodo">
			<input v-model="title" placeholder="add to do..."> </input>
			<input class='btn' type="submit"></input>
		</form>
	</div>
</template>

<script>
	import uuid from 'uuid'
	export default {
		name: "Addtodo",
		data() {
			return {
				title: ''
			}
		},
		methods: {
			addTodo(e) {
				e.preventDefault();
				const newTodo = {
					title: this.title,
					completed:false
				}
				//send up to parent
				this.$emit('add-todo', newTodo);
				this.title = ''

			}
		}
	}
</script>

<style scoped> 
	form {
		display:flex;
	}
	input[type="text"] {
		flex: 10;
		padding:5px;
	}

	input[type="submit"] {
		flex:2;
	}
</style>