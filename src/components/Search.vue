<template>
	<div class="search">
		<input type="text" placeholder="Axtar..." v-model="filter" @keypress.enter="handleSearch" />
		<button @click="handleSearch">Search</button>
	</div>
</template>

<script>
export default {
	name: 'Serach',
	data(){
		return {
			filter:''
		}
	},
	methods:{
		handleSearch(){
         this.$emit('SearchRequested', this.filter)
		}
	}
};
</script>

<style scoped></style>
