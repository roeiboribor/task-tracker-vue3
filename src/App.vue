<template>
	<div class="container">
		<div class="card bg-glass">
			<Header
				title="Task Tracker"
				@toggle-add-task="toggleAddTask"
				:showAddTask="showAddTask"
			/>
			<div v-show="showAddTask">
				<AddTask @add-task="addTask" />
			</div>
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
			showAddTask: false,
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
		toggleAddTask() {
			this.showAddTask = !this.showAddTask;
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
html {
	min-height: 100vh;
}
body {
	font-family: 'Poppins', sans-serif;
	background-repeat: no-repeat;
	background-position: center;
	background-size: cover;
	background-color: #22c1c3;
	background-image: linear-gradient(37deg, #22c1c3 0%, #fdbb2d 100%);
}
.container {
	max-width: 796px;
	margin: 2rem auto;
	overflow: auto;
	min-height: 300px;
	padding: 0.5rem 1rem;
}
.card {
	width: 100%;
	padding: 1rem 2rem;
}
.bg-glass {
	border-radius: 5px;
	background-color: rgba(255, 255, 255, 0.4);
	backdrop-filter: blur(8px);
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
	background: #429c30;
}
.btn-danger {
	background: #c00404;
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
</style>
