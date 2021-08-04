<template>
	<button
		@click="onClick()"
		:class="[showAddTask ? 'btn-danger' : 'btn-success', 'btn']"
	>
		{{ showAddTask ? 'Close' : 'Add Task' }}
	</button>
</template>

<script>
export default {
	name: 'Button',
	props: {
		text: String,
		showAddTask: Boolean,
	},
	methods: {
		onClick() {
			this.$emit('btn-click');
		},
	},
};
</script>
