<template>
  <div class="container" v-if="event">
    <h1>{{ event.title }}</h1>
    <span>{{ event.time }} on {{ event.date }}</span>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "@/services/EventService.js";

export default {
  props: ["id"],
  data() {
    return {
      event: null,
    };
  },
  created() {
    EventService.getEvent(this.id).then((response) => {
      this.event = response.data;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
