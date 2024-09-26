<template>
  <h1>Enter A New Post</h1>
    <div class="page-container">
      <h3>Votes:</h3>
      <input type="text" v-model="votes" />
      <h3>Image:</h3>
      <input type="text" v-model="image"/>
      <h3>Title:</h3>
      <input type="text" v-model="title"/>
      <h3>Author:</h3>
      <input type="text" v-model="author"/>
      <h3>Subreddit:</h3>
      <input type="text" v-model="subreddit"/>
      <br>
      <button @click="submit()">Submit!</button>
    </div>


</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
const router = useRouter()

let votes = ref("")
let image = ref("")
let title = ref("")
let author = ref("")
let subreddit = ref("")




function submit() {

let dataInfo = {
  votes : votes.value,
  image : image.value,
  title : title.value,
  author : author.value,
  subreddit : subreddit.value

}
const params = {
  method: "POST",
  headers: {
    Accept: "application/json",
    "Content-Type": "application/json",
  },

  body: JSON.stringify(dataInfo),
};


  fetch("http://localhost:3000/post", params)
    .then((response) => response.json())
    .then(() => {
    router.push('/')
})
}

</script>






<style scoped>
h1{
  text-align: center;
  color:lightslategray;
}
.page-container {
  display: flex;
  flex-direction: column;
  margin: auto;
  margin-top: 100px;
  align-items: center;
  width: 400px;
  border: 3px solid black;
}
button {
  margin: 30px;
}


</style>
