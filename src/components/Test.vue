<template>
	<div class="test">
		<p>Count :{{ counter }}</p>
		<button v-on:click="incremnetNum">{{ btnText }}</button>
	</div>
</template>

<script>
export default {
	name: 'Test',
	data() {
		return {
			counter: 0,
			message: 'Reverse Message',
		};
	},
	methods: {
		incremnetNum() {
			this.counter += 1;
		},
	},
	props: [ 'btnText'],
};
</script>

<style scoped>
.test {
	color: green;
}
</style>
