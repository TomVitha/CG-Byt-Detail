<script setup>
import { onMounted, ref } from "vue";
import { Carousel } from "@fancyapps/ui";
import "@fancyapps/ui/dist/carousel/carousel.css";
import { cs } from '@fancyapps/ui/dist/carousel/l10n/cs.esm.js';

const carouselRef = ref(null);
const slides = ref([]);

onMounted(() => {
  // Extract slot content as raw HTML
  slides.value = getSlotContent();

  // Initialize Fancyapps Carousel
  if (carouselRef.value) {
    new Carousel(carouselRef.value, {
      transition: "slide",
      infinite: false,
      l10n: cs,
      slidesPerPage: 1,
      // center: false,
      Dots: false,
      classes: {
        container: "f-carousel suggested-apts",
      }
    });
  }
});

// Function to extract slot content as HTML
const getSlotContent = () => {
  return Array.from(carouselRef.value.children).map((child) => child.outerHTML);
};
</script>

<template>
  <div ref="carouselRef" class="f-carousel">
    <div class="f-carousel__slide" v-for="(item, index) in $slots.default()" :key="index">
      <component :is="item"></component>
    </div>
  </div>
</template>

<style>
  .f-carousel.suggested-apts {
    --f-carousel-spacing: 12px;
    --f-custom-slides-per-page: 3;
    --f-carousel-slide-width: calc((100% - calc(var(--f-carousel-spacing) * 2)) / var(--f-custom-slides-per-page));

    width: calc(100% - 30px);
    margin: 0 auto;

    --f-button-next-pos: -30px;
    --f-button-prev-pos: -30px;

    
  }

  @media (max-width: 991px) {
    .f-carousel.suggested-apts {
      --f-custom-slides-per-page: 2;
    }
  }

  @media (max-width: 575px) {
    .f-carousel.suggested-apts {
      --f-custom-slides-per-page: 1;
    }
  }

  .f-carousel.suggested-apts .f-button{
    box-sizing: border-box;
    /* aspect-ratio: 1;
    border-radius: 999px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    cursor: pointer;
    transition: background-color 0.1s;
    font-size: 16px;
    background-color: white;
    border: 1px solid #f1f1f1;
    width:  40px;
    height: 40px; */
  }
</style>