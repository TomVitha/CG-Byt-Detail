<script setup>
  
</script>

<template>
  <nav data-v-09db687c="" aria-label="Breadcrumb">
    <ol data-v-09db687c="" class="breadcrumbs">
      <li data-v-09db687c=""><a data-v-09db687c="" href="/">Hlavní strana</a></li>
      <li data-v-09db687c=""><a data-v-09db687c="" href="/byty-lokality">Přehled projektů</a></li>
      <li data-v-09db687c=""><a data-v-09db687c="" href="/lokalita/189" params="Praha 3 - Žižkov,Rezidence Parková čtvrť">Praha 3 - Žižkov, Rezidence Parková čtvrť</a></li>
      <li data-v-09db687c=""><a data-v-09db687c="" href="/prehled-bytu/189">Ceník bytů</a></li>
      <li data-v-09db687c="" aria-current="page" params="H,117">Byt č. H 117</li>
    </ol>
  </nav>
</template>

<style scoped>

  ul, ol{
    list-style: none;
    padding: 0;
    margin: 0;
    margin: 1rem 0 0 180px;
    display: flex;
    font-size: 0.875rem;
    color: #999;
  }

  li{
    cursor: default;
    user-select: none;

  }

  li+li::before{
    content: '>';
    content: "\F105";
    font-weight: 900;

    font-size: 0.725rem;
    margin: 0 0.4rem;
  }

  a {
    text-decoration: none;
    color: inherit;
    color: var(--color-gray-dark);
    color: var(--color-blue);
    
    &:hover{
      text-decoration: underline;
    }
  }

  /* Font-Awesome icon styling */
  li+li::before{
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    display: var(--fa-display, inline-block);
    font-family: "Font Awesome 6 Pro";
    font-style: normal;
    font-variant: normal;
    line-height: 1;
    text-rendering: auto;
  }



</style>