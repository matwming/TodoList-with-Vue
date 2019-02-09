<template>
  <div>
    <div v-bind:key="el.id" v-for="el in todos">
      <TodoItem v-bind:todo="el" v-on:del-todo="$emit('del-todo',el.id)"/>
    </div>
  </div>
</template>
<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "Todos",
  props: ["todos"],
  components: {
    TodoItem
  }
};
</script>

<style scoped>
</style>


