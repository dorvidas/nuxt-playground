<template>
  <div>
    <ul>
      <li v-for="item in todos" :key="item.id">
        {{ item.title }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data () {
    return {
      todos: []
    }
  },
  async fetch () {
    this.todos = await fetch('https://jsonplaceholder.typicode.com/todos/').then(res => res.json())
  }
}
</script>
