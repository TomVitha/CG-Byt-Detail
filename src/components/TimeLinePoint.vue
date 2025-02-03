<script setup>
  
</script>

<template>
  <div class="timeline__point">
      <span class="timeline__point__name" data-tippy="">
        <!-- <slot name="icon"></slot> -->
        <span>
          <slot name="heading"></slot>
          <!-- <br>
          <slot name="value"></slot> -->
        </span>
      </span>
      <p class="timeline__point__description"><slot name="text"></slot></p>
  </div>
</template>

<style scoped>
  
</style>