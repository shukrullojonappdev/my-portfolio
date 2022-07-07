<template>
  <div class="carousel">
    <button
      v-if="currentSlide !== 1"
      :disabled="currentSlide === 1"
      class="button"
      @click="prevSlide"
    >
      <font-awesome-icon icon="fa-solid fa-angle-left" />
    </button>
    <div class="inner">
      <div v-for="(slide, index) in slides" :key="index" class="cards">
        <div v-show="currentSlide === index + 1" class="card">
          <img
            :src="require(`~/assets/images/${slide.img}.webp`)"
            class="image"
          />
          <div class="text">
            <font-awesome-icon :icon="slide.icon[0]" />
            <font-awesome-icon :icon="slide.icon[1]" />
            <font-awesome-icon :icon="slide.icon[2]" />
            <hr style="margin-top: 15px; margin-bottom: 20px" />
            {{ slide.text }}
          </div>
        </div>
      </div>
    </div>
    <button
      v-if="currentSlide !== 2"
      :disabled="currentSlide === slidesLenth"
      class="button"
      @click="nextSlide"
    >
      <font-awesome-icon icon="fa-solid fa-angle-right" />
    </button>
  </div>
</template>

<script lang="js">

export default {
  name: 'CarouselComponent',
  data() {
    return {
      slides: [
        { img: 'img-1', text: 'Use of the latest technologies during development', icon: ['fa-solid fa-microchip', 'fa-solid fa-laptop-code', 'fa-solid fa-gear']},
        { img: 'img-2', text: 'Development of cross-browser and adaptive sites', icon: ['fa-solid fa-mobile-screen-button', 'fa-solid fa-laptop', 'fa-solid fa-tablet-screen-button']},
      ],
      currentSlide: 1,
      slidesLenth: 2,
    }
  },
  methods: {
    nextSlide() {
      this.currentSlide++
    },
    prevSlide() {
      this.currentSlide--
    },
  }
}
</script>

<style scoped lang="scss">
.carousel {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: -1;
}
.inner {
  width: 100%;
  height: 100vh;
  position: absolute;
  display: flex;
  align-items: center;
  z-index: -2;
}

.cards {
  position: absolute;
  width: 100%;
  height: 100vh;
  z-index: -3;
}
.card {
  position: relative;
  width: 100%;
  min-width: 280px;
  height: 100vh;
  z-index: -4;
  display: flex;
  justify-content: center;
  align-items: center;
}
.image {
  position: absolute;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -5;
  filter: brightness(0.15);
}
.button {
  border: 1px solid white;
  border-radius: 50%;
  background: #00000000;
  padding: 10px 15px;
  position: absolute;
  top: 50%;

  &:first-child {
    left: 0;
    margin-left: 10px;
  }

  &:last-child {
    right: 0;
    margin-right: 10px;
  }
}
.text {
  word-wrap: break-word;
  font-size: 40px;
  padding: 0 80px;
  text-align: center;
}
</style>
