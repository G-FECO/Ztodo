<template>
  <v-app>
    <nav-bar/>
    <v-main>
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
