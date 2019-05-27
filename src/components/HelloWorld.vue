<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p> API Is located at {{ API_URL }} </p>
    <h3>RDS Todos list</h3>
    <ul>
      <li v-for="(todo, index) in todos " :key="index">
        <p> {{ todo.id }} - {{ todo.title }} </p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      API_URL: process.env.VUE_APP_API_URL,
      todos: []
    }
  },
  async created() {
    const res = await axios.get(`${this.API_URL}`)
    this.todos = res.data
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
