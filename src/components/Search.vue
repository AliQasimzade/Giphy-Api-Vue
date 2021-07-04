<template>
  <div class="search">
    <input
      type="text"
      placeholder="Axtar..."
      v-model="filter"
      @keypress.enter="handleSearch"
    />
    <button @click="handleSearch">Search</button>
  </div>
</template>

<script>
export default {
  name: "Serach",
 
  data() {
    return {
      filter: "",
    };
  },
  methods: {
    handleSearch() {
      this.$emit("SearchRequested", this.filter);
    },
	
  },
};
</script>

<style>
.search {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 90px;
  position: sticky;
  top: 0;
  transition: 0.35s background ease-in-out;
}
.search.active{
	background-color: yellow;
}
input {
  border: none;
  outline: none;
  height: 45px;
  background-color: #ccc;
  border-radius: 30px;
  padding-left: 15px;
  width: 50%;
}
input:focus {
  background-color: #000;
  color: #ccc;
}
button {
  height: 45px;
  border: none;
  outline: none;
  background-color: rgb(59, 59, 168);
  color: #fff;
  border-radius: 10px;
  width: 110px;
  margin-left: 5px;
  transition: 0.3s all ease-in-out;
  cursor: pointer;
}
button:hover {
  background-color: rgb(93, 93, 219);
}
</style>
