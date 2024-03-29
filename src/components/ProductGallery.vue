<script setup>
  import { ref } from 'vue'
  import { Swiper, SwiperSlide } from 'swiper/vue'
  import { Thumbs, Navigation } from 'swiper/modules'
  import SwiperCore from 'swiper'
  import 'swiper/css/navigation'
  import 'swiper/css/thumbs'
  import 'swiper/css'

  SwiperCore.use([Navigation, Thumbs])

  const props = defineProps(['product', 'images'])
  const baseUrl = ref(import.meta.env.BASE_URL)
  const thumbsSwiper = ref(null)

  function setThumbsSwiper(swiper) {
    thumbsSwiper.value = swiper
  }
</script>

<template>
  <div class="gallery">
    <div class="gallery__sale">-20%</div>
    <swiper
      :thumbs="{ swiper: thumbsSwiper }"
      navigation
      class="gallery__slider"
    >
      <swiper-slide v-for="photo in images" class="gallery__slide">
        <img :src="baseUrl + photo" class="gallery__image" />
      </swiper-slide>
    </swiper>

    <swiper
      watch-slides-progress
      @swiper="setThumbsSwiper"
      :slides-per-view="3"
      :space-between="10"
      class="gallery__list"
    >
      <swiper-slide v-for="photo in images" class="gallery__item">
        <img :src="baseUrl + photo" class="gallery__preview"/>
      </swiper-slide>
    </swiper>
  </div>
</template>

<style>
  .gallery {
    position: relative;
  }

  .gallery__sale {
    top: 10px;
    position: absolute;
    z-index: 2;
    background-color: #FFC72C;
    color: #38383B;
    font-size: 14px;
    font-weight: bold;
    width: 50px;
    height: 50px;
    border-radius: 50px;
    display: grid;
    align-items: center;
    justify-items: center;
  }

  .gallery__slider {
    height: 580px;
  }

  .gallery__image {
    display: block;
    margin: 0 auto;
    max-width: 100%;
    max-height: 100%;
  }

  .swiper-button-prev::after,
  .swiper-button-next::after {
    font-size: 20px;
    color: #000;
  }

  .gallery__list {
    margin-top: 10px;
  }

  .gallery__item {
    width: 108px !important;
    height: 108px;
    background-color: #F2F2F5;
    padding: 4px;
    cursor: pointer;
    position: relative;
  }

  .gallery__item::after {
    content: '';
    transition: .2s;
    display: block;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #000;
    opacity: 0;
  }
  .gallery__item.swiper-slide-thumb-active::after,
  .gallery__item:hover::after {
    opacity: .3;
  }

  .gallery__preview {
    display: block;
    margin: 0 auto;
    max-width: 100%;
    max-height: 100%;
  }

  @media (max-width: 1024px) {
    .gallery__slider {
      height: 492px;
    }

    .gallery__sale {
      left: 6px;
    }

    .gallery__item {
      width: 78px !important;
      height: 78px;
    }
  }

  @media (max-width: 768px) {
    .gallery__slider {
      height: 426px;
    }

    .gallery__list {
      display: grid;
      justify-content: center;
      margin-top: 16px;
    }

    .gallery__item {
      width: 6px !important;
      height: 6px;
      border-radius: 50%;
      background-color: #CCCCCC;
      margin-right: 16px !important;
    }

    .gallery__item.swiper-slide-thumb-active {
      background-color: #38383B;
    }
    
    .gallery__item::after,
    .gallery__preview {
      display: none;
    }

    .gallery__item.swiper-slide-thumb-active::after,
    .gallery__item:hover::after {
      opacity: .3;
    }
  }
</style>