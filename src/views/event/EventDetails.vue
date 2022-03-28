<template>
  <div class="container" v-if="event">
    <h1>{{ event.title }}</h1>
    <span>{{ event.time }} on {{ event.date }}</span>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
export default {
  props: ["event"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
