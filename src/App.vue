<template>
  <Navbar />
  <Event :text="text" />
  <SearchBar :data="data_temp" @searchMovie="searchMovie($event)" />
  <div class="btn-all">
    <button @click="showAllMovie">전체보기</button>
  </div>
  <Movies
    :data="data_temp"
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
import SearchBar from "./components/SearchBar.vue";

export default {
  name: "App",
  data() {
    return {
      isModal: false,
      data: movieData, //원본
      data_temp: [...movieData],
      selectedMovie: 0,
      text: "NEPLIX 강렬한 운명의 드라마, 경기의 크리처!!",
    };
  },
  methods: {
    increaseLike(id) {
      this.data.find((movie) => {
        if (movie.id == id) {
          movie.like += 1;
        }
      });
    },
    searchMovie(title) {
      //영화 제목이 포함된 데이터를 가져옴.
      this.data_temp = this.data.filter((movie) => {
        return movie.title.includes(title);
      });
    },
    showAllMovie() {
      this.data_temp = [...this.data];
    },
  },
  components: {
    Navbar: Navbar,
    SearchBar: SearchBar,
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

.btn-all {
  display: flex;
  justify-content: center;
}
</style>
