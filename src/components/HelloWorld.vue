<template>
  <div class="gifs-container">
    <div class="gif" v-for="gif in gifs" :key="gif">
      <a :href="gif.media[0].gif.url" target="_blank">
        <img :src="gif.media[0].gif.url" />
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["gifs"],
};
</script>

<style>
.gifs-container {
  width: 100%;
  background-color: #ccc;
  display: grid;
  grid-template-columns: repeat(3,1fr);
  grid-template-rows: 1fr;
  
}
.gif {

  height: 220px;
  cursor: pointer;
  margin: 8px;
  transition: 0.3s all ease-in-out;
}
.gif:hover {

  box-shadow: -1px 1px 46px -4px rgba(11, 0, 0, 0.75);
  -webkit-box-shadow: -1px 1px 46px -4px rgba(11, 0, 0, 0.75);
  -moz-box-shadow: -1px 1px 46px -4px rgba(11, 0, 0, 0.75);
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
