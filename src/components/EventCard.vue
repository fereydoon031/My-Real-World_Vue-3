<template>
  <router-link
    class="event-link"
    :to="{ name: 'EventDetails', params: { id: event.id } }"
  >
    <div class="card">
      <div class="container" v-if="event">
        <h4>{{ event.title }}</h4>
        <span>{{ event.time }} on {{ event.date }}</span>
        <p>{{ event.description }}</p>
      </div>
    </div>
  </router-link>
</template>

<script>
export default {
  props: {
    event: {
      type: Object,
      required: true,
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card {
  box-shadow: 4px 13px 30px 1px rgba(97, 97, 97, 0.2);
  transition: 0.3s;
  display: inline-block;
  flex-direction: column;
  align-items: center;
  border-radius: 7px;
  margin: 10px;
}

.card:hover {
  box-shadow: 4px 13px 30px 1px rgba(85, 221, 131, 0.2);
}

.container {
  padding: 2px 16px;
}

.image {
  height: 200px;
}

.event-link {
  color: #2c3e50;
  text-decoration: none;
}
</style>
