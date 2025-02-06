<script setup>

</script>

<template>
  <div class="breadcrumbs-wrapper container-m">
    <div class="breadcrumbs">
      <ul>
        <li><a href="#"><i class="fa-light fa-house" title="Domov" aria-hidden="true"></i><span class="sr-only">Domov</span></a></li>
        <li><a href="#" title="Přehled všech projektů">Projekty</a></li>
        <li><a href="#" title="Rezidence Basilejské náměstí">Rezidence Basilejské náměstí</a></li>
        <li><a href="#" title="Ceník">Ceník</a></li>
        <li>D64</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
  /* ? Breadcrumbs */
  .breadcrumbs {
    display: block;
    margin: 0px;
    overflow: auto;
    white-space: nowrap;
    width: 100%;
    scrollbar-color: #00000044 transparent;
    scrollbar-width: none;

    margin-bottom: -0.75rem;
  }

  @supports not (scrollbar-width: none) {
    @media screen and (max-width: 400px) {
      .breadcrumbs {
        display: block;
      }
    }
  }

  .breadcrumbs>ul {
    padding: 8px 0px 0px 16px;
    margin: 4px 0 0;
    list-style-type: none;
  }

  .breadcrumbs li {
    display: inline-block;
    font-size: .875rem;
    cursor: default;
    -webkit-user-select: none;
    user-select: none;
  }

  .breadcrumbs li:first-child {
    margin-left: 117px;
  }

  .breadcrumbs li:last-child {
    font-weight: 300;
    margin-right: 10px;
  }

  @media (min-width: 575px) {
    .breadcrumbs>ul {
      margin-top: 8px;
    }

    .breadcrumbs li:first-child {
      margin-left: 150px;
    }
  }

  @media (min-width: 992px) {
    .breadcrumbs>ul {
      margin-top: 7px;
    }

    .breadcrumbs li:first-child {
      margin-left: 180px;
    }
  }

  .breadcrumbs li+li:before{
    content: '>';
    content: "\F105";
    font-weight: 900;

    font-size: 0.725rem;
    margin: 0 0.4rem;
  }

  .breadcrumbs a {
    text-decoration: none;
  }

  .breadcrumbs a:hover {
    text-decoration: underline;
  }

  .breadcrumbs-light li {
    color: #fff;
  }

  .breadcrumbs-light a,
  .breadcrumbs-light li+li:before {
    color: #fff;
  }


  nav a.nav-brand {
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0.0);
  }

  /* Font-Awesome icon styling */
  li+li::before{
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    display: var(--fa-display, inline-block);
    font-style: normal;
    font-variant: normal;
    line-height: 1;
    text-rendering: auto;
    font-family: "Font Awesome 6 Pro";
  }
</style>