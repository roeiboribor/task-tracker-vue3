<template>
	<div class="container">
		<Header title="Task Tracker" />
		<AddTask @add-task="addTask" />
		<p class="tip">
			<b>Tip: </b>
			Double Tap to set reminder!
		</p>
		<Tasks
			@toggle-reminder="toggleReminder"
			@delete-task="deleteTask"
			:tasks="tasks"
		/>
	</div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
	name: 'App',
	components: {
		Header,
		Tasks,
		AddTask,
	},
	data() {
		return {
			tasks: [],
		};
	},
	methods: {
		addTask(task) {
			this.tasks = [...this.tasks, task];
		},
		deleteTask(id) {
			if (confirm('Are you sure to delete this task?')) {
				this.tasks = this.tasks.filter((task) => task.id !== id);
			}
		},
		toggleReminder(id) {
			this.tasks = this.tasks.map((task) =>
				task.id == id ? { ...task, reminder: !task.reminder } : task
			);
		},
	},
	created() {
		this.tasks = [
			{
				id: 1,
				text: 'Take out the trash',
				datetime: '08/05/2021, 6:30 PM',
				reminder: true,
			},
			{
				id: 2,
				text: 'Clean the windows',
				datetime: '08/06/2021, 6:00 AM',
				reminder: true,
			},
			{
				id: 3,
				text: 'Cook for lunch',
				datetime: '08/07/2021, 11:30 AM',
				reminder: false,
			},
			{
				id: 4,
				text: 'Buy some groceries',
				datetime: '08/08/2021, 09:00 AM',
				reminder: false,
			},
			{
				id: 5,
				text: 'Paint the roof top',
				datetime: '08/09/2021, 10:00 AM',
				reminder: true,
			},
		];
	},
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
body {
	font-family: 'Poppins', sans-serif;
}
.container {
	max-width: 500px;
	margin: 30px auto;
	overflow: auto;
	min-height: 300px;
	border: 1px solid steelblue;
	padding: 30px;
	border-radius: 5px;
}
.tip {
	margin-bottom: 1rem;
}
.btn {
	display: inline-block;
	background: #000;
	padding: 10px 20px;
	margin: 5px;
	color: #fff;
	border: none;
	border-radius: 5px;
	cursor: pointer;
	text-decoration: none;
	font-size: 15px;
	font-family: inherit;
}
.btn-success {
	background: transparent;
	padding: 0;
	margin: 0;
	color: #429c30;
}
.btn:focus {
	outline: none;
}
.btn:active {
	transform: scale(0.98);
}
.btn-block {
	display: block;
	width: 100%;
}
.noselect {
	-webkit-touch-callout: none; /* iOS Safari */
	-webkit-user-select: none; /* Safari */
	-khtml-user-select: none; /* Konqueror HTML */
	-moz-user-select: none; /* Old versions of Firefox */
	-ms-user-select: none; /* Internet Explorer/Edge */
	user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}
</style>
