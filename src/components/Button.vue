<template>
	<button @click="onClick()" class="btn btn-success">
		<i class="bx bxs-plus-square bx-lg"></i>
	</button>
</template>

<script>
export default {
	name: 'Button',
	props: {
		color: String,
	},
	methods: {
		onClick() {
			console.log('Add!');
		},
	},
};
</script>
