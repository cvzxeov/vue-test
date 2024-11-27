<template>
    <div>
      <h1>Главная страница</h1>
      <h3>Персонажи</h3>
      <div class="slider">
        <div class="slides" :style="{ transform: `translateX(-${currentSlide * 100}%)` }">
          <div class="slide" v-for="(image, index) in images" :key="index">
            <img :src="image" alt="Слайд" />
          </div>
        </div>
        <button class="prev" @click="prevSlide">&#10094;</button>
        <button class="next" @click="nextSlide">&#10095;</button>
      </div>
      <h2>Компании, которые пользуются нашими товарами:</h2>
      <ul>
        <li>VALORANT</li>
        <li>DEADLOOK</li>
        <li>CS:GO 2</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        currentSlide: 0,
        images: [
          'https://avatanplus.com/files/resources/original/5670093fe95a8151a5a421d4.png',
          'https://d2sbsqqdu2ofn4.cloudfront.net/media/images/Mars_Png_Side_350px.max-400x400.png',
          'https://dota2.su/media/photos/video/brewmaster.png'
        ]
      };
    },
    methods: {
      nextSlide() {
        this.currentSlide = (this.currentSlide + 1) % this.images.length;
      },
      prevSlide() {
        this.currentSlide = (this.currentSlide - 1 + this.images.length) % this.images.length;
      }
    },
    mounted() {
      setInterval(this.nextSlide, 5000); // автоматическое переключение слайдов каждые 5 секунд
    }
  };
  </script>
  
  <style scoped>
  .slider {
    position: relative;
    overflow: hidden;
    width: 100%;
  }
  
  .slides {
    display: flex;
    transition: transform 0.5s ease-in-out;
  }
  
  .slide {
    min-width: 100%;
  }
  
  .slide img {
    width: 100%;
    height: auto;
  }
  
  button.prev, button.next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(255, 255, 255, 0.7);
    border: none;
    cursor: pointer;
  }
  
  button.prev {
    left: 10px;
  }
  
  button.next {
    right: 10px;
  }
  </style>