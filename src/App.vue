<template>
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
    </div>
  </div>
  <!-- <p v-for="(item, i) in foods" :key="i">{{ item }}</p> -->
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      like: 0,
      // foods: ["김밥", "순대", "만두", "떡볶이"],
      data: [
        {
          title: "노량",
          year: 2023,
          category: "액션, 드라마",
          textRed: "color: red",
          like: 0,
          imgUrl: "./assets/noryang.jpg",
        },
        {
          title: "아쿠아맨과 로스트 킹덤",
          year: 2023,
          category: "액션, 판타지, 어드밴처",
          like: 0,
          imgUrl: "./assets/aquaman.jpg",
        },
        {
          title: "3일의 휴가",
          year: 2023,
          category: "판타지, 드라마",
          like: 0,
          imgUrl: "./assets/ourseason.jpg",
        },
      ],
    };
  },
  methods: {
    increaseLike(i) {
      this.data[i].like += 1;
    },
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
