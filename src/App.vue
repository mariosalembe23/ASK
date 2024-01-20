<script>
import Navbar from "./components/Navbar.vue";
import Main from "./components/Main.vue";
export default {
  components: {
    Navbar,
    Main
  },
};
</script>

<template>
  <div class="w-full h-full flex retrato-tablet:flex-row flex-col items-center">
    <Navbar />
    <Main/>
  </div>
</template>

<style scoped></style>
