<template>
  <div class="container">
    <h1>영화정보</h1>
    <div v-for="movie in data" :key="movie.id" class="item">
      <figure>
        <img :src="`${movie.imgUrl}`" :alt="movie.title" />
      </figure>
      <div class="info">
        <h3>{{ movie.title }}</h3>
        <p>개봉: {{ movie.year }}</p>
        <p>장르: {{ movie.category }}</p>
        <button v-on:click="$emit('increaseLike', movie.id)">좋아요</button>
        <span>{{ movie.like }}</span>
        <p>
          <button @click="$emit('openModal', movie.id)">상세보기</button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesComponent",
  props: {
    data: Array,
  },
};
</script>

<style>
.container {
  padding: 20px;
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
