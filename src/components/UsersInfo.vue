<template>
	<div class="container">
		
	</div>
</template>

<script>
export default {
	name: 'UsersInfo',
	data() {
		return {
			users: [
				{
					name: 'Ali',
					surname: 'Qasimzade',
					age: 21,
				},
				{
					name: 'Rahil',
					surname: 'Aliyev',
					age: 23,
				},
				{
					name: 'Eldar',
					surname: 'Babayev',
					age: 27,
				},
			],
		};
	},
	props:['gifs'],
	computed: {
		totalAges() {
			let resultAges = 0;
			this.users.forEach((item) => {
				resultAges += item.age;
			});
			return resultAges;
		},
	},
};
</script>

<style scoped>
.container {
	display: flex;
}
.info {
	width: 250px;
	height: 250px;
	background-color: grey;
	border-radius: 4px;
	display: flex;
	flex-direction: column;
	align-content: center;
	justify-content: center;
	margin: 12px;
}
</style>
