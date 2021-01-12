<template>
  <div class="header">
    <AppHeader />
  </div>
  <div class="container">
    <Calendar />
  </div>
</template>

<script>
import Calendar from "./components/Calendar";
import AppHeader from "./components/AppHeader";

export default {
  name: "App",
  components: {
    Calendar,
    AppHeader,
  },
};
</script>

<style lang="scss"></style>
