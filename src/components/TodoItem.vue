<template>
  <div class="todo-item">
    <b-form-checkbox
      :id="`checkBox-${item.key}`"
      v-model="item.checked"
      :name="`checkBox-${item.key}`"
      value="1"
      unchecked-value="0"
    >
      {{ item.value }}
    </b-form-checkbox>
    <b-button v-on:click="deleteEvent()">Borrar</b-button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    item: Object
  },
  methods: {
    deleteEvent() {
      this.$emit('delete-item', this.item);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.todo-item {
  text-align: left;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0.4rem 0;
  &:first {
    margin-top: 1rem;
  }
}
</style>
