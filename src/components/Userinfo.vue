<script setup>
import { ref } from 'vue';

const props = defineProps(["post"]);


const id = ref(props.post.id)
const votes = ref(props.post.votes)


function downVote(){
votes.value--
updateVotes()
}

function upVote(){
  votes.value++
  updateVotes()
}



function updateVotes(){
const params = {
method: "PUT",
body: JSON.stringify({votes: votes.value}),
headers: {
Accept: "application/json",
"Content-Type": "application/json"
}
}


fetch(`http://localhost:3000/post/${id.value}`, params)
.then(response => {return response.json()})
.then(data => {
  votes.value = data.votes

})
}





</script>

<template>
  <div class="layout">
    <div>
      <img @click="upVote()"
        class="upvote"
        src="https://preview.redd.it/you-do-not-need-to-upvote-this-post-there-is-literally-no-v0-np7tgmxmz7pb1.png?width=640&crop=smart&auto=webp&s=5f75a3d2d10e7d189ed04b7912e76dccfe92aafe"
      />
      <img @click="downVote()"
        class="downvote"
        src="data:image/png;base64,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"
      />
    </div>
    <div class="votes">
      <p>{{ votes }}</p>
    </div>
    <div>
      <img class="user-image" :src="post.image" />
      <p>{{ post.title }}</p>
      <p>{{ post.author }}</p>
      <p>{{ post.subreddit }}</p>
    </div>
  </div>
</template>

<style scoped>
.user-image {
  width: 50px;
  height: 50px;
  display: flex;
}

.layout {
  display: flex;
  margin: 50px;
}

.upvote,
.downvote {
  width: 50px;
  height: 50px;
  display: flex;
  flex-direction: row;
  
}

.votes {
  margin: 30px;
}
</style>

