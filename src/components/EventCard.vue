<template>
  <div class="card">
    <img class="image" src="../assets/img_avatar.png" />
    <div class="container">
      <h4><b>John Doe</b></h4>
      <p>Architect & Engineer</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "EventCard",
  props: {
    msg: String,
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
  box-shadow: 4px 13px 30px 1px rgba(48, 47, 47, 0.2);
}

.container {
  padding: 2px 16px;
}

.image {
  height: 200px;
}
</style>
