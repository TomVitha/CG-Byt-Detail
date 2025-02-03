<script setup>
    // import { RouterLink } from 'vue-router'
</script>

<template>
    <header>
        <div class="header__top">
            <div class="container">
                <div class="logo--container">
                    <RouterLink to="/" class="logo--wrapper">
                        <img class="logo" src="https://central-group.cz/wms3/img/logo-cg.a68b84d3.svg" alt="CENTRAL GROUP" title="Homepage" />
                    </RouterLink>
                </div>
                <div>
                    <RouterLink class="header__top-item" to="/home">BYTY</RouterLink>
                    <RouterLink class="header__top-item" to="/about">KOMERCE</RouterLink>
                </div>
            </div>
        </div>
        <div class="header__bottom">
            <div class="container">
                <RouterLink class="header__bottom-item" to="/">v1</RouterLink>
                <RouterLink class="header__bottom-item" to="/home2">v2</RouterLink>
            </div>
        </div>
    </header>
</template>

<style scoped>
    header {
        position: sticky;
        top: 0;
        z-index: 999;
        color: white;
    }

    header a{
        color: inherit;
        text-decoration: none;
    }

    .header__top {
        background-color: #20234c;
        height: 55px;
    }

    .header__top>div {
        display: flex;
        align-items: center;
        height: 100%;
        gap: 15px;
        padding-inline: 30px;
    }

    /* <div> */
    .logo--container,
    .logo{
        width: 148px;
        height: auto;
    }
    /* <a> */
    .logo--wrapper{       
        position: absolute;
        top: 0px;
        left: 30px;
    }

    /* <img> */
    .logo {
        /* width: 100%;
        height: 100%; */
        object-fit: cover;
    }

    .header__top-item{
        display: inline-block;
        height: 100%;
        padding: 15px;

        &:hover{
            background-color: #414366;
        }
    }

    .header__bottom {
        background-color: #0e1237;
        height: 39px;
    }

    .header__bottom > div {
        display: flex;
        align-items: center;
        height: 100%;
        gap: 15px;
        padding-inline: 30px;
        padding-left: 205px;
    }

    @media screen and (max-width: 991px) {
        .logo--container,
        .logo{
            width: 120px;
        }

        .header__bottom {
            display: none;
        }

        .header__top-item{
            visibility: hidden;
        }
    }

    @media screen and (max-width: 575px) {
        .logo--container,
        .logo{
            width: 100px;
        }
    }
</style>