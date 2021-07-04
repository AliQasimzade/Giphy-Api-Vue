<template>
  <p v-if="isLoading">Loading...</p>
  <Search v-on:SearchRequested="handleSearch" v-if="!isLoading" />
  <HelloWorld :gifs="gifs" v-if="!isLoading" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Search from "./components/Search.vue";

export default {
  name: "App",
  data: () => ({
    isLoading: true,
    gifs: [],
  }),
  methods: {
    handleSearch(filter) {
      this.gifs = [];
      this.isLoading = true;
      fetch(`https://g.tenor.com/v1/search?q=${filter}&key=LIVDSRZULELAtrending`)
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
    fetch("https://g.tenor.com/v1/trending?key=LIVDSRZULELA")
      .then((res) => {
        return res.json();
      })
      .then((res) => {
        console.log(res.results);
        this.gifs = res.results;
        setTimeout(() => {
          this.isLoading = false;
        }, 500);
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
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
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
