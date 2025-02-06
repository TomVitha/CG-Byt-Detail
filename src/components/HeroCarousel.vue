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
/* ! NOT SCOPED ! */

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


  @media screen and (min-width: 576px) {
    .f-button {
      --f-button-next-pos: 10px;
      --f-button-prev-pos: 10px;
      --f-button-bg: white;
      --f-button-hover-bg: white;
      --f-button-border-radius: 999px;
      /* --f-button-border: 1px solid #f1f1f1; */
      --f-button-width:   36px;
      --f-button-height:  36px;
      --f-button-svg-width:   20px;
      --f-button-svg-height:  20px;
    }
  }

  &.has-dots{
    margin-bottom: 0;
  }

  .f-carousel__dots{
    bottom: 0;
  }

  .f-carousel__slide{
    max-height: 500px;
  }

  .f-carousel__slide>*{
    height: 100%;
  }

  .f-carousel__slide>figure{
    max-height: inherit;
    height: inherit;
    position: relative;
    padding: 16px 0px calc(var(--f-carousel-dots-height, 30px) + 1.25rem);
    margin-inline: auto;

    figcaption {
      position: absolute;
      bottom: var(--f-carousel-dots-height, 30px);
      left: 0;
      right: 0;
      color: inherit;
      text-align: center;
      display: block;
      margin: 0 auto;
      /* background: linear-gradient(0deg, rgb(255, 255, 255) 0%, rgba(255, 255, 255, 0) 100%); */
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
    top:    16px;
    left:   18px;
    width:  36px;
    height: 36px;
    mix-blend-mode: multiply;
    border-radius: 999px;
  }

  .gallery-slide-grid{
    display: grid;
    grid-template-columns: 1fr 1fr 36%;
    grid-template-rows: 1fr 1fr;
    max-width: 100%;
    gap: 8px;
    padding: 0 !important;
    transition-property: scale, opacity;
    transition-duration: 0.45s;
    transition-timing-function: ease-out;
    

    &:hover{
      scale: 1.025;
      opacity: 0.65;
    }
  }

  .gallery-slide-grid__main{
    grid-column: span 2;
    grid-row: span 2;
    max-width: 100%;
    object-fit: cover;

  }

  .gallery-slide-grid__aside{
    max-width: 100%;
    object-fit: cover;
  }
}


</style>
