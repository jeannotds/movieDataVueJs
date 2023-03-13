<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/movie/tt0409591">
        <img src="../assets/story.jpg" class="feature-img" />
        <div class="detail">
          <h3>Naruto</h3>
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Adipisci
            dolorum obcaecati neque iure unde deleniti quos sit laborum culpa
            veniam repellendus labore consequatur placeat eligendi dignissimos
            aliquid accusantium, illum accusamus.
          </p>
        </div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: "HomeView",
  components: {},
};
</script>

<style>
.feature-card {
  position: relative;
}
.feature-img {
  display: block;
  width: 100%;
  height: 300px;
  opacity: 0.4;
  object-fit: cover;
  position: relative;
  z-index: 0;
}

.detail {
  position: absolute;
  /* top: 0; */
  right: 0;
  left: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.6);
  padding: 16px;
  z-index: 1;
}

h3{
  color: rgba(255, 255, 255, 0.67);
  margin-bottom: 16px;
}

p{
  color: rgba(255, 255, 255, 0.67);
  margin-bottom: 16px;
}

</style>
