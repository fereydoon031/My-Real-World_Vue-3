<template>
  <div class="container" v-if="event">
    <div id="nav">
      <router-link :to="{ name: 'EventDetails' }">Details </router-link>
      |
      <router-link :to="{ name: 'EventRegister' }">Register </router-link>
      |
      <router-link :to="{ name: 'EventEdit' }">Edit </router-link>
    </div>
    <router-view :event="event" />
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
