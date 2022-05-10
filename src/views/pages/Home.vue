<template>
  <tasks />
</template>

<script lang="ts">
import Vue from "vue";
import Tasks from "../components/Terms.vue";

export default Vue.extend({
  name: "Home",

  components: {
    Tasks,
  },
});
</script>
