<template>
  <div>
    <input v-model="newItem" type="text">
    <button @click="addItem">Add</button>
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
      newItem: '',
      todos: []
    }
  },
  async fetch () {
    const items = await fetch('https://jsonplaceholder.typicode.com/todos/').then(res => res.json())
    this.todos = items.slice(0, 20)
  },
  methods: {
    addItem () {
      this.todos.push({
        id: this.todos.length,
        title: this.newItem
      })
      this.newItem = ''
    }
  }
}
</script>
