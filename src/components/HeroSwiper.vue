<script>
  // Import Swiper Vue.js components
  import { Swiper, SwiperSlide } from 'swiper/vue';

  // Import Swiper styles
  import 'swiper/css';

  import 'swiper/css/pagination';
  import 'swiper/css/navigation';

  // import './style.css';

  // import required modules
  import { Keyboard, Pagination, Navigation } from 'swiper/modules';

  export default {
    components: {
      Swiper,
      SwiperSlide,
    },
    setup() {
      return {
        keyboard: {
          enabled: true,
        },
        pagination: {
          clickable: true,
          renderBullet: function (index, className) {
            return `<button class="${className}" role="button" aria-label="Go to slide ${(index + 1)}">${(index + 1)}</span>`;
          },
        },
        modules: [Keyboard, Pagination, Navigation],
      };
    },
  };
</script>

<template>
  <swiper
    ref="swiperRef"
    :loop="true"
    :slidesPerView="1"
    :spaceBetween="0"
    :keyboard="keyboard"
    :pagination="pagination"
    :navigation="true"
    :modules="modules"
    class="hero-swiper"
    id="hero-swiper"
  >                
    <swiper-slide v-for="(item, index) in $slots.default()" :key="index">
      <component :is="item"></component>
    </swiper-slide>
  </swiper>
</template>

<style>
  .swiper {
    width: 100%;
    height: 500px;
    /* max-height: 500px; */
    /* height: calc( min(1110px, 100vw) / var(--swiper-slide-aspect-ratio, 1.5) ); */
  }

  @media screen and (max-width: 991px) {
    .swiper {
      height: 400px;
    }
  }

  @media screen and (max-width: 575px) {
    .swiper {
      height: 325px;
    }
  }

  .swiper-slide {
    text-align: center;
    font-size: 18px;
    background: #fff;

    /* Center slide text vertically */
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .swiper-slide img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  .swiper-pagination-bullet {
    width: 20px;
    height: 20px;
    text-align: center;
    line-height: 20px;
    font-size: 12px;
    color: #000;
    opacity: 1;
    background: rgba(0, 0, 0, 0.2);
    user-select: none;
  }

  .swiper-pagination-bullet-active {
    color: #fff;
    background: #007aff;
  }


</style>