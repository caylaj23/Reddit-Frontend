<script setup>
import { useRouter } from 'vue-router';
const router = useRouter()
import { reactive } from "vue";
import Userinfo from "@/components/Userinfo.vue";

const userDisplay = reactive([]);

fetch("http://localhost:3000/")
.then(response => {
  return response.json()
})
    .then(data => {
      userDisplay.push(...data)
    });


</script>

<template>
    <header>
       <img
        id="reddit-logo"
        src="https://www.reddiquette.com/wp-content/uploads/2020/09/What-Is-The-Reddit-Logo-Called.png"/>
    <h1>Reddit</h1>
    <h4>Home</h4>
    <h4>New</h4>
    <h4>Rising</h4>
    <h4>Controversial</h4>
    <h4>Top</h4>
    <h4>Wiki</h4>
  </header>



<div class="info-container">
  <Userinfo v-for="post in userDisplay" :post="post"></Userinfo>
</div>
</template>

<style scoped>
h1{
  color: orangered;
}
header {
  display: flex;
  justify-content: space-evenly;
 align-items: end;
  background-color: lightblue;
}

#reddit-logo {
  height: 50px;
  width: 50px;
  display: flex;
  justify-content: start;
}

.info-container {
  border: 2px gray solid;
  
}
</style>
