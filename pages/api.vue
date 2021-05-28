<template>
 <div class="page">
   <ul class="data-list">
     <li v-for="post in posts" :key="post.id">
        <p><span>title:</span>{{ post.title }}</p>
        <p><span>body:</span>{{ post.body }}</p>
     </li>
   </ul>
 </div>
</template>

<script>
import axios from 'axios'

export default {
 data () {
   return {
     posts: [],
   }
 },
 mounted () {
   axios.get('https://jsonplaceholder.typicode.com/posts')
     .then((response) => this.posts = response.data)
 }
}
</script>

<style>
.data-list li {
    margin-bottom: 20px;
}

.data-list p {
    margin-bottom: 5px;
}

.data-list span {
    font-weight: bold;
}

</style>
