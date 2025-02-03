<script setup>
import { ref, computed } from 'vue';

const isInFavorites = ref(false);

function toggleFavorite() {
  isInFavorites.value = !isInFavorites.value;
}

const favoriteTooltip = computed(() => 
  isInFavorites.value ? 'Odstranit z oblíbených' : 'Přidat do oblíbených'
);
</script>

<template>
  <a href="https://example.com" target="_blank" class="card-apt">
      <div class="card-apt__fav">
          <i 
            :class="['fav-add', 'fa-heart', isInFavorites ? 'fas' : 'fal']" 
            :data-tippy-content="favoriteTooltip" 
            @click.prevent="toggleFavorite"
          ></i>
      </div>
      <section class="card-apt__thumbnail">
          <img class="card-apt__compass" src="https://www.central-group.cz/uloziste/80/804f5c80-cc09-4457-8f65-bf9b13ebd68f.gif" alt="" srcset="">
          <img class="card-apt__thumbnail-img" src="https://www.central-group.cz/uloziste/d8/d8e7fdfa-ce14-4160-a10c-bce634f6f45a.gif" alt="" srcset="">
      </section>
      <section class="card-apt__heading">
          <h3 class="card-apt__big-info">
              C&nbsp;133
          </h3>
          <span class="status status--available">Volný</span>
      </section>
      <section class="card-apt__location">
          <h4>Harfa Living</h4>
          <h5>Praha 9 - Vysočany</h5>
      </section>
      <section class="card-apt__specs">
          <dl class="dl-grid">
              <dt>Patro</dt>
              <dd>1. patro</dd>
              <dt>Dispozice</dt>
              <dd>1+kk</dd>
              <dt>Plocha</dt>
              <dd>32&nbsp;m²</dd>
              <dt>B/T/Z</dt>
              <dd>4,9&nbsp;m²</dd>
              <dt>Termín dokončení</dt>
              <dd>prosinec 2026</dd>
              <!-- <dt>Akční sleva</dt> -->
              <!-- <dd>120.000&nbsp;Kč</dd> -->
          </dl>
      </section>
      <section class="card-apt__price">
          <dl>
              <dt class="sr-only">Cena vč. DPH</dt>
              <dd class="d-flex align-items-center">
                  <strong class="card-apt__big-info" data-tippy-content="Cena vč. DPH. Nezahrnuje přiřazené příslušenství.">4.158.560&nbsp;Kč</strong>
                  <!-- "Sloupec Bonus (Dárek)" -->
                  <!-- <span data-tippy-content="Parkovací stání zdarma">
                      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" style="fill:#20234c; height: 0.85rem; padding-inline: 0.5rem;"><path d="M190.5 68.8L225.3 128H224 152c-22.1 0-40-17.9-40-40s17.9-40 40-40h2.2c14.9 0 28.8 7.9 36.3 20.8zM64 88c0 14.4 3.5 28 9.6 40H32c-17.7 0-32 14.3-32 32v64c0 17.7 14.3 32 32 32H480c17.7 0 32-14.3 32-32V160c0-17.7-14.3-32-32-32H438.4c6.1-12 9.6-25.6 9.6-40c0-48.6-39.4-88-88-88h-2.2c-31.9 0-61.5 16.9-77.7 44.4L256 85.5l-24.1-41C215.7 16.9 186.1 0 154.2 0H152C103.4 0 64 39.4 64 88zm336 0c0 22.1-17.9 40-40 40H288h-1.3l34.8-59.2C329.1 55.9 342.9 48 357.8 48H360c22.1 0 40 17.9 40 40zM32 288V464c0 26.5 21.5 48 48 48H224V288H32zM288 512H432c26.5 0 48-21.5 48-48V288H288V512z"></path></svg>
                  </span> -->
              </dd>
          </dl>
      </section>
  </a>
</template>

<style scoped>

.card-apt{
    background-color: white;
    border-radius: 10px;
    color: var(--color-gray-dark);
    /* ? for some reason to na prod stránce hází na display: block, proto important */
    display: flex !important;
    flex-direction: column;
    font-size: 0.875rem;
    gap: 0.5rem;
    /* box-shadow: 0px 0px 0px 1px #f1f1f1; */
    border: 1px solid #f1f1f1;
    /* hidden used as fallback for clip */
    overflow: hidden; 
    overflow: clip;
    padding: 1.0rem 1.25rem;
    position: relative;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    transition: background-color 150ms, filter 150ms;
    line-height: 1.15;
}

@media (pointer: coarse), not (hover: hover){
    .card-apt:active{
        /* background-color: #f9f9f9; */
        filter: brightness(95%);
    }
}


.card-apt__big-info{
    font-size: 1.25rem;
    color: var(--color-blue);
    font-weight: 700;
    line-height: 1.15;
    margin: 0;
}

a.card-apt,
.card-apt a{
    text-decoration: none;
    color: inherit;
}

.card-apt a:hover{
    text-decoration: underline;
}

.card-apt h4 {
    font-size: 1.125rem;
    color: var(--color-blue);
    margin-bottom: 0.0em;
    font-weight: 700;
    line-height: 1.15;
}

.card-apt h5 {
    font-size: 1rem;
    color: var(--color-blue);
    margin: 0;
    font-weight: 400;
}

.card-apt .card-apt__specs{
    flex-grow: 1;
}


.card-apt__thumbnail-img {
    width: auto;
    height: 9rem;
    aspect-ratio: 4/3;
    object-fit: contain;
    object-position: center;
    padding: 0.25rem 0 0.625rem;
    margin: 0 auto;
}

@supports not (aspect-ratio: 4/3) {
    .card-apt__thumbnail-img{
	    max-width: min(12rem, 100%);
    }
}

/* Růžice */
.card-apt__compass{
    position: absolute;
    display: block;
    width: 1.5rem;
    mix-blend-mode: multiply;
    object-fit: contain;
}

.card-apt__heading{
    color: var(--color-blue, #20234c);
    display: flex;
    align-items: center;
    gap: 0.25em 0.5em;
    justify-content: left;
    flex-wrap: wrap-reverse;
}


.card-apt__heading [class*="fa-"]{
    font-size: 1rem;
    margin-bottom: -0.1em;
}


.card-apt dl.dl-grid{
    display: grid;
    grid-template-columns: 2fr 3fr;
    align-items: baseline;
    margin: 0;
    gap: 0.3em 0.6em;
}

.card-apt dt{
    font-size: 0.875rem;
    font-weight: 400;
}

.card-apt dd{
    font-size: 1rem;
    font-weight: 650;
    line-height: 1;
}


.card-apt .label{
    display: block;
    line-height: 1.25;
}


.card-apt .card-apt__fav{
    position: absolute;
    top: 0rem;
    right: 0rem;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0);

}

/* If browser supports :has() selector */
@supports selector(:has(*)){
    /* and if device is capable of hover and uses mouse */
    @media (hover: hover) and (pointer: fine){
        /* hides heart by default */
        .card-apt .card-apt__fav{
            display: none;
        }
        /* shows heart on hover */
        .card-apt:hover .card-apt__fav{
            display: block;
        }
        /* heart stays visible if active */
        .card-apt .card-apt__fav:has(.fa-heart.fas){
            display: block;
        }
    }
}

/* Heart icon general */
.card-apt__fav .fa-heart{
    cursor: pointer;
    color: var(--color-gray-dark);
    transition: color 75ms, scale 150ms;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    font-size: 1.25rem;
    padding: 16px 18px;
    border-radius: 0 16px 0 16px; 
}


/* When primary pointer is fine (cursor, pen) */
@media (pointer: fine) {

    /* Smaller hitbox for heart icon */
    .card-apt__fav .fa-heart{
        margin: 12px 14px;
        padding: 4px;
    }
    .card-apt__fav i.fal:hover {
        color: var(--color-heart);
    }
}

.card-apt__fav .fa-heart:hover:active {
    scale: 75%;
    color: var(--color-heart);
}

/* Add to fav - heart fill */
.card-apt__fav .fa-heart.fas{
    color: var(--color-heart);
    animation-name: heart-fill;
    animation-duration: 125ms;
}

/* Remove from fav - heart pop */
.card-apt__fav .fa-heart.fal { 
    animation-name: heart-pop;
    animation-duration: 100ms;
}


</style>