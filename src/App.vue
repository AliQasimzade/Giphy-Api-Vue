<template>
	<p v-if="isLoading">Loading...</p>
	<Search v-on:SearchRequested="handleSearch" />
	<HelloWorld :gifs="gifs" />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import Search from './components/Search.vue';

export default {
	name: 'App',
	data: () => ({
		isLoading: true,
		gifs: [],
	}),
	methods: {
		handleSearch(filter) {
			this.gifs = [];
			this.isLoading = true;
			fetch(`https://g.tenor.com/v1/search?q=${filter}&key=LIVDSRZULELA`)
			.then((res) => {
				return res.json();
			})
			.then((res) => {
				console.log(res.results);
				this.gifs = res.results;
				this.isLoading = false;
			});
		},
	},
	created() {
		fetch('https://g.tenor.com/v1/trending?key=LIVDSRZULELA')
			.then((res) => {
				return res.json();
			})
			.then((res) => {
				console.log(res.results);
				this.gifs = res.results;
				this.isLoading = false;
			});
	},
	components: {
		HelloWorld,
		Search,
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

.img {
	animation: spin 1.3s infinite linear;
}
@keyframes spin {
	0% {
		transform: rotate(0deg);
	}
	100% {
		transform: rotate(360deg);
	}
}
</style>
