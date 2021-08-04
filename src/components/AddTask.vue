<template>
	<form @submit="onSubmit" class="add-form">
		<div class="form-control">
			<label>Task</label>
			<input type="text" v-model="text" name="text" placeholder="Add Task" />
		</div>
		<div class="form-control">
			<label>Date & Time</label>
			<input
				type="datetime-local"
				v-model="datetime"
				name="datetime"
				placeholder="Select Date & Time"
				required
			/>
		</div>
		<div class="form-control form-control-check">
			<label>Set Reminder</label>
			<input type="checkbox" v-model="reminder" name="reminder" />
		</div>

		<button type="submit" class="btn btn-block">
			Save Task <i class="bx bxs-save bx-sm"></i>
		</button>
	</form>
</template>

<script>
import Button from './Button.vue';
export default {
	components: { Button },
	name: 'AddTask',
};
</script>

<style scoped>
.bx {
	vertical-align: middle;
}
.add-form {
	margin-bottom: 40px;
}
.form-control {
	margin: 20px 0;
}
.form-control label {
	display: block;
}
.form-control input {
	width: 100%;
	height: 40px;
	margin: 5px;
	padding: 3px 7px;
	font-size: 17px;
}
.form-control-check {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
.form-control-check label {
	flex: 1;
}
.form-control-check input {
	flex: 1;
	height: 20px;
}
</style>
