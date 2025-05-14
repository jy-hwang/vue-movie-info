<template>
  <Navbar />
  <Event :text="text" />
  <Movies
    :data="data"
    @openModal="
      isModal = true;
      selectedMovie = $event;
    "
    @increaseLike="increaseLike($event)"
  />

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
import Movies from "./components/Movies.vue";

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
    Movies: Movies,
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
</style>
