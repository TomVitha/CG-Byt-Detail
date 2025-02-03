<script setup>
  // import { RouterLink } from 'vue-router'
</script>

<template>
  <footer>
    <div class="footer__top">
      <div class="container">
        footer
      </div>
    </div>
    <div class="footer__bottom">
      <div class="container"></div>
    </div>
  </footer>
</template>

<style scoped>
  footer{
   color: var(--color-blue, #20234c);
  }
  .footer__top {
    background-color: #f2f2f2;
    min-height: 412px;
  }
  .footer__bottom{
    background-color: #e4e4e4;
    min-height: 84px;
  }
</style>