<template>
	<div class="hello">
		<h1 v-if="isLoading">Loading ...</h1>
		<h1 v-if="!isLoading">{{ msg }}</h1>
		<UsersInfo :gifs=gifs />
	</div>
</template>

<script>
import UsersInfo from './UsersInfo.vue';
export default {
	name: 'HelloWorld',
	data() {
		return {
			gifs:[],
			isLoading: true,
		};
	},
	props: {
		msg: {
			type: Number,
			required: false,
		},
	},
	components:{
		UsersInfo
	},
	created(){
		fetch('http://api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC')
		.then(res =>  res.json())
		.then(res => this.gifs = res.data)
	}
};
</script>

<style scoped>
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
</style>
