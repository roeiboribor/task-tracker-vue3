<template>
	<div v-for="(task, index) in tasks" :key="index">
		<Task :task="task" />
	</div>
</template>

<script>
import Task from './Task.vue';
export default {
	name: 'Tasks',
	props: {
		tasks: Array,
	},
	components: {
		Task,
	},
};
</script>
