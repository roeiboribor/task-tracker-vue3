<template>
	<div
		@dblclick="$emit('toggle-reminder', task.id)"
		:class="[task.reminder ? 'reminder' : '', 'task']"
	>
		<h3>
			{{ task.text }}
			<i @click="$emit('delete-task', task.id)" class="bx bxs-trash bx-sm"></i>
		</h3>
		<p>
			{{ `${task.month} ${task.date} ${task.time}` }}
		</p>
	</div>
</template>

<script>
export default {
	name: 'Task',
	props: {
		task: Object,
	},
	/* methods: {
		// Longer Process onDelete(task.id)
		onDelete(id) {
			this.$emit('delete-task', id);
		},
	}, */
};
</script>

<style scoped>
.bxs-trash {
	color: red;
}
.bxs-alarm {
	cursor: pointer;
	color: cornflowerblue;
}
.task {
	background: #f4f4f4;
	margin: 5px;
	padding: 10px 20px;
	cursor: pointer;
}
.task.reminder {
	border-left: 5px solid green;
}
.task h3 {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
</style>
