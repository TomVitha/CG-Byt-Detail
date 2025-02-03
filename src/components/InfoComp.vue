<script setup>

</script>

<template>
  <div class="info-comp">
    <div class="info-comp__icon">
      <slot name="icon"></slot>
    </div>
    <div class="info-comp__details">
      <span class="info-comp__heading">
        <slot name="heading"></slot>
      </span>
      <span class="info-comp__value">
        <slot name="text"></slot>
      </span>
    </div>
  </div>
</template>

<style scoped>
.info-comp {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 0.75rem 20px;
  line-height: 1;
}

/* Hides icon's container if no icon provided (to avoid gap) */
:is(.info-comp__icon, .info-comp__details, .info-comp__value):empty{
  display: none;
}


/* Made for <img>, <svg> and Font Awesome icons */
.info-comp__icon > * {
  --info-comp__icon-size: 24px;
  text-align: center;
  font-size: var(--info-comp__icon-size, 1.5rem);
  height: var(--info-comp__icon-size, 1.5rem);
  width: calc(var(--info-comp__icon-size, 1.5rem) + 0.25rem);
  object-fit: contain;
  /* fill: var(--color-blue, #20234c); */
  color: var(--color-blue, #20234c);
  --fa-primary-color: currentColor;
  --fa-primary-opacity: 1.0;
  --fa-secondary-color: #ffffff;
  --fa-secondary-opacity: 0.99;
}


.info-comp__details {
  display: flex;
  flex-direction: column;
  line-height: 1.20;
}

.info-comp__heading {
  font-weight: 400;
  font-size: 1rem;
}

.info-comp__value {
  font-weight: 700;
  font-size: 0.875rem;
}

@media screen and (max-width: 991px) {

  .info-comp {
    gap: 1em;
  }
}


/* inverts #heading and #text text-weight  */
.info-comp.invert{
  .info-comp__heading {
    font-weight: 700;
    /* font-size: 0.875rem; */
  }

  .info-comp__value {
    font-weight: 400;
    /* font-size: 1rem; */
  }
}

.info-comp.inline{
  display: inline-flex;
}

.info-comp.vertical{
  flex-direction: column;
  text-align: center;
}

a.card{
  text-decoration: none;
}


.info-comp.circle{
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  width: 100%;
  /* max-width: 150px; */
  isolation: isolate;

  /* flex: 1 1 auto; */

  .info-comp__icon{
    position: relative;
    isolation: isolate;
    border-radius: 999px;
    width:  58px;
    height: 58px;
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;

    background-color: #e5eef6;
    background-color: #e7f1f8;
    background-color: #ebf3f9;
  }


  .info-comp__icon > *{
    /* --info-comp__icon-size: 26px; */
    /* color: #fff; */
    /* fill: #fff; */
    width: auto;
  }
}




</style>