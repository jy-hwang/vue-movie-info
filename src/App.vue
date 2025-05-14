<template>
  <Navbar />
  <Event :text="text" />
  <h1>영화정보</h1>
  <div v-for="(movie, i) in data" :key="i" class="item">
    <figure>
      <img :src="`${movie.imgUrl}`" :alt="movie.title" />
    </figure>
    <div class="info">
      <h3>{{ movie.title }}</h3>
      <p>개봉: {{ movie.year }}</p>
      <p>장르: {{ movie.category }}</p>
      <button v-on:click="increaseLike(i)">좋아요</button
      ><span>{{ movie.like }}</span>
      <p>
        <button
          @click="
            isModal = true;
            selectedMovie = i;
          "
        >
          상세보기
        </button>
      </p>
    </div>
  </div>
  <Modal
    :data="data"
    :isModal="isModal"
    :selectedMovie="selectedMovie"
    @closeModal="isModal = false"
  />
</template>

<script>
import movieData from "./assets/movies";
import Navbar from "./components/Navbar.vue";
import Modal from "./components/Modal.vue";
import Event from "./components/Event.vue";

export default {
  name: "App",
  data() {
    return {
      isModal: false,
      data: movieData,
      selectedMovie: 0,
      text: "NEPLIX 강렬한 운명의 드라마, 경기의 크리처!!",
    };
  },
  methods: {
    increaseLike(i) {
      this.data[i].like += 1;
    },
  },
  components: {
    Navbar: Navbar,
    Modal: Modal,
    Event: Event,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px;
}

h1,
h2,
h3 {
  margin-bottom: 1rem;
}

p {
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-top: 1rem;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
}

.item .info {
  width: 100%;
}
</style>
