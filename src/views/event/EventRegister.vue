<template>
  <p>Register for the event</p>
  <button @click="register()">Register Me</button>
</template>

<script>
export default {
  props: ["event"],
  methods: {
    register() {
      //call to API

      this.$router.push({
        name: "EventDetails",
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
