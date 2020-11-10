<template>
  <v-app>
    <nav-bar/>
    <v-main class="bg">
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
import NavBar from "@/layouts/NavBar"

export default {
  name: 'App',
  components: {
    NavBar,
  },
  data: () => ({
  }),
};
</script>

<style>
.bg {
  background-color: dimgrey;
}
</style>