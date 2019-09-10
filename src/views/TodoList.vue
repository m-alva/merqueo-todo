<template>
  <div class="todo-list">
    <b-form-input v-model="inputText" placeholder="Descripción de la tarea" v-on:keyup.enter="insertItem"></b-form-input>
    <TodoItem v-for="item of todoList" v-bind:key="item.key" :item="item" v-on:delete-item="deleteItem"/>
  </div>
</template>

<script>
// @ is an alias to /src
import TodoItem from '@/components/TodoItem.vue'

export default {
  name: 'home',
  data() {
    return {
      inputText: '',
      todoList: []
    }
  },
  components: {
    TodoItem
  },
  methods: {
    insertItem() {
      this.todoList.push({
        key: this.todoList.length,
        value: this.inputText,
        checked: false,
      });
      this.inputText = '';
    },
    deleteItem(item) {
      this.todoList.splice(this.todoList.indexOf(obj => obj.key === item.key),1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.todo-list {
  width: 100%;
  max-width: 300px;
  margin-left: auto;
  margin-right: auto;
  padding: 0 0.8rem;
}
</style>
