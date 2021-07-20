<template>
  <p v-if="isLoading">Loading...</p>
  <Search v-on:SearchRequested="handleSearch" :str="str" />
  <h3 v-if="str">{{ `${str} total result(${gifs.length}) :` }}</h3>
  <HelloWorld :gifs="gifs" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Search from "./components/Search.vue";

export default {
  name: "App",
  data: () => ({
    isLoading: true,
    gifs: [],
    str: "",
    isShow: false,
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
      this.isShow = true;
      this.str = filter;
    },
  },
  created() {
    
    fetch("https://g.tenor.com/v1/trending?key=LIVDSRZULELA")
      .then((res) => {
        return res.json();
      })
      .then((res) => {
        console.log(res.results);
        this.gifs = res.results;
        setTimeout(() => {
          this.isLoading = false;
        }, 400);
      });

    window.addEventListener("scroll", () => {
      if (
        document.body.scrollTop > 0 ||
        document.documentElement.scrollTop > 0
      ) {
        document.querySelector(".search").classList.add("active");
      } else {
        document.querySelector(".search").classList.remove("active");
      }
    });
  },
  components: {
    HelloWorld,
    Search,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
