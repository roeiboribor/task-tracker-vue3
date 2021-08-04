<template>
	<div class="container">
		<Header title="Task Tracker" />
		<p>
			<b>Tip: </b>
			Double Tap to set reminder!
		</p>
		<Tasks :tasks="tasks" />
	</div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';

export default {
	name: 'App',
	components: {
		Header,
		Tasks,
	},
	data() {
		return {
			tasks: [],
		};
	},
	created() {
		this.tasks = [
			{
				id: 1,
				text: 'Take out the trash',
				month: 'August',
				date: '03',
				time: '2:30 PM',
				reminder: true,
			},
			{
				id: 2,
				text: 'Clean the windows',
				month: 'September',
				date: '01',
				time: '9:30 PM',
				reminder: true,
			},
			{
				id: 3,
				text: 'Cook for lunch',
				dmonth: 'November',
				date: '19',
				time: '2:30 PM',
				reminder: false,
			},
			{
				id: 4,
				text: 'Buy some groceries',
				month: 'December',
				date: '25',
				time: '11:00 AM',
				reminder: false,
			},
			{
				id: 5,
				text: 'Paint the roof top',
				month: 'January',
				date: '13',
				time: '10:30 AM',
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
.btn {
	display: inline-block;
	background: transparent;
	color: #000;
	border: none;
	border-radius: 5px;
	cursor: pointer;
	text-decoration: none;
	font-size: 15px;
	font-family: inherit;
}
.btn-success {
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
