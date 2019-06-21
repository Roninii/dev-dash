<template>
  <v-app :dark="dark">
    <v-content>
      <Welcome/>
    </v-content>
  </v-app>
</template>

<script>
import Welcome from "./components/Welcome";

export default {
  name: "App",
  components: {
    Welcome
  },
  data() {
    return {
      dark: true
    };
  }
};
</script>
