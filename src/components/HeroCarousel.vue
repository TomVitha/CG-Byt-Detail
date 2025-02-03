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
      l10n: cs,
      Dots: {
        dotTpl: '<button type="button" data-carousel-page="%i" aria-label="{{GOTO}}"><span class="f-carousel__dot" aria-hidden="true"></span></button>',
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
/* WIP */

#hero-carousel {

  /* height: 500px; */
  /* --f-carousel-slide-height: 100%; */

  /* max-height: 500px; */

  --f-carousel-slide-aspect-ratio: 1.5;
  --f-carousel-slide-max-width: var(--container-max-width, 1110px);
  --f-carousel-slide-width: min(var(--f-carousel-slide-max-width), 100vw);
  --f-carousel-slide-height: calc( var(--f-carousel-slide-width) / var(--f-carousel-slide-aspect-ratio) );

  --f-button-next-pos: 0px;
  --f-button-prev-pos: 0px;

  .f-carousel__slide{
    max-height: 500px;
    /* max-height: 100%; */
  }

  .f-carousel__slide>*{
    height: 100%;
    /* aspect-ratio: var(--f-carousel-slide-aspect-ratio); */
  }

  .f-carousel__slide>figure{
    max-height: inherit;
    height: inherit;
    position: relative;
    padding-bottom: 2rem;
    margin-inline: auto;

    figcaption {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      color: inherit;
      text-align: center;
      display: block;
      margin: 0 auto;
      background: linear-gradient(0deg, rgb(255, 255, 255) 0%, rgba(255, 255, 255, 0) 100%);
      font-size: 0.875rem;
    }
  }

  img {
    width: 100%;
    height: 100%;
    display: block;
    object-fit: contain;
    object-position: center center;
    max-width: 85%;
    margin-inline: auto;
  }

  .compass {
    position: absolute;
    top:    0px;
    left:   18px;
    width:  36px;
    height: 36px;
    mix-blend-mode: multiply;
    border-radius: 999px;
  }
}
</style>
