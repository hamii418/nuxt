<template>
<div class="api">
  <h1>jsonplaceholderからapi取得</h1>
  <table>
    <tr v-for="post in posts" :key=post.id>
        <td>{{ post.userId }}</td>
        <td>{{ post.title }}</td>
    </tr>
  </table>
</div>
</template>

<style>
.api h1 {
  font-size: 2rem;
  text-align: center;
  margin-top: 50px;
}

.api table {
  max-width: 800px;
  margin: 50px auto;
  font-size: 16px;
  border-top: 1px solid;
  border-left: 1px solid;
}

.api table td {
  padding: 10px;
  border-right: 1px solid;
  border-bottom: 1px solid;
}

</style>

<script>
import axios from 'axios';

export default {
  data(){
    return {
      posts: []
    }
  },
  mounted(){
    axios.get('https://jsonplaceholder.typicode.com/posts')
          .then(response => this.posts = response.data);
  }
}
</script>