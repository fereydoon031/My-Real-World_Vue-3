<template>
  <div class="home">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
  <div class="pagination">
    <router-link
      id="page-prev"
      :to="{ name: 'home', query: { page: page - 1 } }"
      rel="prev"
      v-if="page != 1"
    >
      &#60; Previous
    </router-link>
    <router-link
      id="page-next"
      :to="{ name: 'home', query: { page: page + 1 } }"
      rel="next"
      v-if="hasNextPage"
    >
      Next &#62;
    </router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js";
import NProgress from "nprogress";
export default {
  name: "HomeView",
  props: ["page"],
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
      totalEvents: 0,
    };
  },
  beforeRouteEnter(routeTo, routeFrom, next) {
    NProgress.start();
    EventService.getEvents(2, parseInt(routeTo.query.page) || 1)
      .then((response) => {
        next((comp) => {
          comp.events = response.data;
          comp.totalEvents = response.headers["x-total-count"];
        });
      })
      .catch(() => {
        next({ name: "NetworkError" });
      })
      .finally(() => {
        NProgress.done();
      });
  },
  beforeRouteUpdate(routeTo) {
    NProgress.start();
    EventService.getEvents(2, parseInt(routeTo.query.page) || 1)
      .then((response) => {
        this.events = response.data;
        this.totalEvents = response.headers["x-total-count"];
      })
      .catch(() => {
        return { name: "NetworkError" };
      })
      .finally(() => {
        NProgress.done();
      });
  },
  computed: {
    hasNextPage: function () {
      var totalPages = Math.ceil(this.totalEvents / 2);

      return this.page < totalPages;
    },
  },
};
</script>

<style scoped>
.pagination {
  display: inline-flex;
  width: 50%;
}

.pagination a {
  flex: 1;
  text-decoration: none;
  color: #2c3e50;
}

#page-prev {
  text-align: left;
}

#page-next {
  text-align: right;
}
</style>
