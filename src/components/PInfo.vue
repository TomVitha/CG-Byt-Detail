<script setup>

</script>

<template>
  <div class="p-info">
    <div class="p-info__icon">
      <slot name="icon"></slot>
    </div>
    <div class="p-info__details">
      <span class="p-info__heading">
        <slot name="heading"></slot>
      </span>
      <span class="p-info__value">
        <slot name="text"></slot>
      </span>
    </div>
  </div>
</template>

<style scoped>
.p-info {
  display: flex;
  align-items: center;
  gap: 1rem;
  line-height: 1;
}

.p-info__icon {
  --size: 1.5rem;
  color: var(--color-blue);
  font-size: var(--size, 1.5rem);
  height: var(--size, 1.5rem);
  width: auto;
  /* aspect-ratio: 1; */
  /* margin: auto; */
  text-align: right;

  /* temp */
  /* display: none; */
}


.p-info__details {
  display: flex;
  flex-direction: column;
  /* align-items: center; */
  /* gap: 0.25rem; */
  line-height: 1.20;
}

.p-info__heading {
  font-size: 0.875rem;
}

.p-info__value {
  font-weight: 700;
  font-size: 0.875rem;
}

@media screen and (max-width: 991px) {
  .p-info {
    gap: 0.75rem;
  }

  .p-info__icon {
    height: 1.5rem;
    font-size: 1.5rem;
  }
}

.p-info__icon img {
  height: 100%;
  /* width: auto; */
}
</style>