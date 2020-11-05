<template>
  <v-row>
    <v-col>
      <todo-list></todo-list>
    </v-col>
  </v-row>
</template>

<script>
import TodoList from "@/components/TodoList";

export default {
  name: 'Home',
  components: {
    TodoList
  }
}
</script>
