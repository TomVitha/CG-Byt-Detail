<script setup>
  import { ref, computed } from "vue";

  import InfoComp from '../components/InfoComp.vue'
  import Tabs from '../components/tabs/CTabs.vue'
  import Tab from '../components/tabs/CTab.vue'
  import TimeLine from '../components/TimeLine.vue'
  import TimeLinePoint from '../components/TimeLinePoint.vue'
  // import SpecsTable1 from '../components/SpecsTable1.vue'
  import SpecsTable2 from '../components/SpecsTable2.vue'
  import SpecsTable3 from '../components/SpecsTable3.vue'
  // import Breadcrumbs from '../components/BreadCrumbs.vue'
  import BreadcrumbsMy from '../components/BreadCrumbsMy.vue'
  import AptCard from '../components/AptCard.vue'
  import FancyBox from '../components/FancyBox.vue'
  import HeroCarousel from '../components/HeroCarousel.vue'
  import SuggestedApts from '../components/SuggestedApts.vue'
  import HeroSwiper from '../components/HeroSwiper.vue'

  const urokovaSazba = 0.0479;
  const cenaBytu = ref(8796113);
  const vyseUveru = computed(() => 
    (cenaBytu.value - vlastniZdroje.value)
  )
  const vlastniZdroje = ref(5000000);
  const splatnost = ref(10);
  const mesicniSplatka = computed(() => 
    (vyseUveru.value / splatnost.value / 12) 
  )


  const shareDataThisPage = {
    title: document.title,
    text: document.title,
    url: location.href,
  };

  const sharePage = async (data = shareDataThisPage) => {
    if (navigator.share){
      try {
        await navigator.share(data);
      } catch (error) {
        console.log(error)
        // Show fallback window
      }
    } else {
      // Show fallback window
    }
  }

  const jv = ref(1);

  const formatCurrency = (value, jv) => {
      let locale;
      switch (jv) {
        case 2:
          locale = 'ru-RU';
          break;
        case 3:
          locale = 'en-US';
          break;
        case 1:
        default:
          locale = 'cs-CZ';
      }
      return new Intl.NumberFormat(locale, { style: 'currency', currency: 'CZK' }).format(value);
    };

    const formatYear = (year, jv) => {
      let locale;
      let yearWord;
      switch (jv) {
        case 2:
          locale = 'ru-RU';
          if (year === 1) {
            yearWord = 'год';
          } else if (year > 1 && year < 5) {
            yearWord = 'года';
          } else  {
            yearWord = 'лет';
          }
          break;
        case 3:
          locale = 'en-US';
          if (year === 1) {
            yearWord = 'year';
          } else {
            yearWord = 'years';
          }
          break;
        case 1:
        default:
          locale = 'cs-CZ';
          if (year === 1) {
            yearWord = 'rok';
          } else if(year > 1 && year < 5) {
            yearWord = 'roky';
          } else {
            yearWord = 'let';
          }
      }
      return `${new Intl.NumberFormat(locale).format(year)} ${yearWord}`;
    }




</script>

<template>
  <!-- Here's where the magic happens -->
  <main>

    <section>
      <div class="container">
        <!-- <Breadcrumbs /> -->
        <BreadcrumbsMy />
      </div>
    </section>

    <section>
      <div class="headings container">
        <div class="heading">
          <!-- <h1>Byt&nbsp;A37</h1> -->
          <h1>A37</h1>
          <span class="status status--available dot">Volný</span>
        </div>
      </div>
    </section>

    <section class="main-map" id="e21">
      <div class="container">
        <div class="prim-in card">
          <div class="prim-img--container">
            <img class="prim-img" src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" alt="Půdorys bytu">
          </div>
          <div class="prim-rack--aside">
            <!-- Next to main img -->
            <img src="https://www.central-group.cz/Uloziste/65/65e9beaf-588a-4e65-8d60-fb603db6ca41.png" alt="Půdorys podlaží">
            <img src="https://www.central-group.cz/Uloziste/55/55a0d1a4-ba33-4b27-a971-6735f2dda742.gif" alt="Pohled na dům s vyznačením patra">
            <img src="https://www.central-group.cz/Uloziste/cc/cc3ee842-a5c6-4180-a29c-5d887155e470.png" alt="Situační plánek lokality">
          </div>
        </div>
      </div>
    </section>

    <section class="main-map" id="e20">
      <div class="container">
        <div class="card" style="padding: 4px 12px 0px;">
          <Tabs>
            <Tab title="Půdorys">
              <div class="prim-img--container">
                <img class="prim-img" src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" alt="Půdorys bytu">
              </div>
            </Tab>
            <Tab title="3. patro">
              <div class="prim-img--container">
                <img class="prim-img" src="https://www.central-group.cz/Uloziste/b4/b45dcd22-898d-4c88-a0b4-0bbb3f27cbc7.png" alt="Půdorys podlaží">
              </div>
            </Tab>
            <Tab title="Dům A">
              <div class="prim-img--container">
                <img class="prim-img" src="https://www.central-group.cz/Uloziste/55/55a0d1a4-ba33-4b27-a971-6735f2dda742.gif" alt="Pohled na dům s vyznačením patra">
              </div>
            </Tab>
            <Tab title="Lokalita">
              <div class="prim-img--container">
                <img class="prim-img" src="https://www.central-group.cz/Uloziste/8f/8fff6b6e-772c-4278-9f6f-47b7f798135f.png" alt="Situační plánek lokality">
              </div>
            </Tab>
          </Tabs>
        </div>
      </div>
    </section>

    <!-- Ještě jeden pokus o carousel -->
    <section class="main-map2" id="e23">
      <div class="container">
        <!-- <h3>Carousel</h3> -->
        <div class="card">
          <HeroCarousel class="hero-carousel" id="hero-carousel" >
            <figure>
              <!-- <img src="https://www.central-group.cz/Uloziste/6b/6bade729-b37e-4514-9a51-0dfcf5540b1e.gif" alt="Půdorys bytu"> -->
              <img src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" alt="Půdorys bytu">
              <!-- <img src="https://www.central-group.cz/Uloziste/a9/a92dca27-5c76-4c14-8c00-be36387e59a7.gif" alt="Půdorys bytu"> -->
              <img class="compass" src="https://www.central-group.cz/Uloziste/08/08ab4610-c285-49ce-9a99-ab274d4ad9e8.gif" alt="">
              <figcaption>Půdorys bytu</figcaption>
            </figure>
            <figure>
              <img src="https://www.central-group.cz/Uloziste/b4/b45dcd22-898d-4c88-a0b4-0bbb3f27cbc7.png" alt="Půdorys podlaží">
              <figcaption>Půdorys podlaží</figcaption>
            </figure>
            <figure>
              <img src="https://www.central-group.cz/Uloziste/f6/f627eb50-6daa-4a99-97b4-9ba39834274e.gif" alt="Pohled na dům s vyznačením patra">
              <figcaption>Pohled na dům s vyznačením patra</figcaption>
            </figure>
            <figure style="background-color: #e5e5e5;">
              <img src="https://www.central-group.cz/Uloziste/3d/3d5c0ab0-eae8-4d67-aa14-b24bc60ec086.png" alt="Situační plánek lokality">
              <figcaption>Situační plánek lokality</figcaption>
            </figure>
            <a href="#e18" class="gallery-slide-grid">
              <!-- <img src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" class="gallery-slide-grid__main" style="padding: 1rem; object-fit: contain;" alt="Půdorys bytu"> -->
              <img src="https://picsum.photos/id/1000/2000/1250" class="gallery-slide-grid__main" alt="">
              <img src="https://picsum.photos/id/1010/2000/1250" class="gallery-slide-grid__aside" alt="">
              <img src="https://picsum.photos/id/1020/2000/1250" class="gallery-slide-grid__aside" alt="">
            </a>
          </HeroCarousel>
        </div>
      </div>
    </section>

    <!-- SWIPER -->
    <section id="e39">
      <div class="container">
        <!-- <h3>Swiper</h3> -->
        <div class="card">
          <HeroSwiper>
            <img src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" alt="Půdorys bytu">
            <img src="https://www.central-group.cz/Uloziste/b4/b45dcd22-898d-4c88-a0b4-0bbb3f27cbc7.png" alt="Půdorys podlaží">
            <img src="https://www.central-group.cz/Uloziste/f6/f627eb50-6daa-4a99-97b4-9ba39834274e.gif" alt="Pohled na dům s vyznačením patra">
            <img src="https://www.central-group.cz/Uloziste/3d/3d5c0ab0-eae8-4d67-aa14-b24bc60ec086.png" alt="Situační plánek lokality">
          </HeroSwiper>
        </div>
      </div>
    </section>


    <section>
      <div class="container">
        <div class="main-layout">
          <div>
            <section id="e19">
              <div class="overview">
                <div>
                  <h2>
                    <span>Rezidenční čtvrť Tesla Hloubětín</span>
                    <span>Praha&nbsp;9 &#8209; Hloubětín</span>
                  </h2>
                  <div class="trinity">
                    <div>
                      <abbr title="Dispozice"><i class="far fa-border-all"></i></abbr>
                      <span>2+kk</span>
                    </div>
                    <div>
                      <abbr title="Podlaží"><i class="far fa-building"></i></abbr>
                      <span>3. patro</span>
                    </div>
                    <div>
                      <abbr title="Celková plocha"><i class="far fa-ruler-combined"></i></abbr>
                      <span>174&nbsp;m²</span>
                    </div>
                  </div>
                  <div class="price">
                    <strong>8.796.113&nbsp;Kč</strong>
                  </div>
                  <p class="stealth">Všechny ceny jsou uváděny včetně DPH.</p>
                </div>
                <div class="actions">
                  <!-- Fav -->
                  <button class="action fav" onclick="$(this).find('i').toggleClass('fal fas')"><i class="fal fa-heart"></i></button>
                  <!-- Hypo -->
                  <a href="#hypo3" class="action"><i class="fa-light fa-calculator"></i></a>
                  <!-- Share -->
                  <button class="action" @click="sharePage().prevent" ><i class="fa-light fa-arrow-up-from-bracket"></i></button>
                </div>
              </div>
            </section>

            <!-- Trinity as Card w/ separators - DEPRECATED -->
            <section id="e1">
              <div class="info-comps separators card">
                <InfoComp>
                  <template #icon>
                    <i class="fa-light fa-border-all"></i>
                    <!-- <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="100 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g transform="scale(1.2)"> <g> <g> <path d="M92.867,425.667h204.8h204.8c5.12,0,8.533-3.413,8.533-8.533v-153.6v-153.6V7.533C511,2.413,507.587-1,502.467-1H340.333 h-93.867h-153.6c-5.12,0-8.533,3.413-8.533,8.533v204.8V280.6V383v34.133C84.333,422.253,87.747,425.667,92.867,425.667z M101.4,289.133h85.333c-4.267,45.227-40.107,81.067-85.333,85.333V289.133z M101.4,16.067h136.533v51.2H229.4 c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h34.133c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533H255 v-51.2h76.8v93.867c0,5.12,3.413,8.533,8.533,8.533h34.133V127c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533V92.867 c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533v8.533h-25.6V16.067h145.067V101.4H459.8v-8.533 c0-5.12-3.413-8.533-8.533-8.533c-5.12,0-8.533,3.413-8.533,8.533V127c0,5.12,3.413,8.533,8.533,8.533 c5.12,0,8.533-3.413,8.533-8.533v-8.533h34.133V255h-51.2v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533V280.6 c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533v-8.533h51.2V408.6H306.2V272.067h51.2v8.533 c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533v-34.133c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533V255 h-59.733c-5.12,0-8.533,3.413-8.533,8.533V408.6H101.4v-17.388c57.425-4.332,102.4-52.044,102.4-110.612 c0-5.12-3.413-8.533-8.533-8.533H101.4v-51.2h145.067c5.12,0,8.533-3.413,8.533-8.533V152.6h8.533 c5.12,0,8.533-3.413,8.533-8.533c0-5.12-3.413-8.533-8.533-8.533H229.4c-5.12,0-8.533,3.413-8.533,8.533 c0,5.12,3.413,8.533,8.533,8.533h8.533v51.2H101.4V16.067z"></path></g></g></g></g></svg> -->
                    <!-- <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 330.004 330.004" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M315.002,0h-300c-8.284,0-15,6.716-15,15v300.004c0,8.284,6.716,15,15,15h170c8.284,0,15-6.716,15-15 c0-8.284-6.716-15-15-15h-155v-130h70V225c0,8.284,6.716,15,15,15s15-6.716,15-15V85c0-8.284-6.716-15-15-15s-15,6.716-15,15v55.004 h-70V30h150v75.004c0,8.284,6.716,15,15,15h70c8.284,0,15-6.716,15-15c0-8.284-6.716-15-15-15h-55V30h90v180.004h-105 c-8.284,0-15,6.716-15,15c0,8.284,6.716,15,15,15h105v60h-25c-8.284,0-15,6.716-15,15c0,8.284,6.716,15,15,15h40 c8.284,0,15-6.716,15-15V15C330.002,6.716,323.286,0,315.002,0z"></path> </g></svg> -->
                     <!-- <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M512,60.746C512,27.194,484.806,0,451.254,0c-33.551,0-60.746,27.194-60.746,60.746h-34.712H190.915h-60.746H8.678 C3.885,60.746,0,64.631,0,69.424v208.271v52.068v104.136v69.424C0,508.115,3.885,512,8.678,512h130.169h208.271h104.656 C485.031,512,512,485.031,512,451.775c0-0.115-0.008-0.227-0.008-0.341c0.001-0.061,0.008-0.118,0.008-0.179V60.746z M407.864,60.746c0-23.966,19.424-43.39,43.39-43.39c23.966,0,43.39,19.424,43.39,43.39v347.993 c-6.259-6.387-13.919-11.392-22.48-14.531c-0.102-0.037-0.206-0.069-0.308-0.106c-0.824-0.297-1.653-0.583-2.493-0.845 c-0.235-0.073-0.476-0.134-0.712-0.205c-0.715-0.213-1.431-0.426-2.157-0.614c-0.358-0.093-0.722-0.167-1.082-0.253 c-0.617-0.147-1.232-0.301-1.856-0.429c-0.454-0.093-0.915-0.165-1.373-0.248c-0.541-0.098-1.079-0.207-1.625-0.291 c-0.548-0.084-1.103-0.144-1.655-0.213c-0.466-0.059-0.929-0.13-1.398-0.178c-0.661-0.068-1.331-0.108-1.998-0.154 c-0.369-0.026-0.734-0.065-1.105-0.084c-1.042-0.053-2.091-0.081-3.146-0.081c-16.998,0-32.365,6.98-43.39,18.231V69.424V60.746z M17.356,338.441h86.392c-4.119,45.835-40.557,82.272-86.392,86.392V338.441z M451.775,494.644h-95.978v-95.458 c0-4.793-3.885-8.678-8.678-8.678h-60.746v-8.678c0-4.793-3.885-8.678-8.678-8.678c-4.793,0-8.678,3.885-8.678,8.678v34.712 c0,4.793,3.885,8.678,8.678,8.678c4.793,0,8.678-3.885,8.678-8.678v-8.678h52.068v86.78H147.525v-86.78h52.068v8.678 c0,4.793,3.885,8.678,8.678,8.678s8.678-3.885,8.678-8.678v-34.712c0-4.793-3.885-8.678-8.678-8.678s-8.678,3.885-8.678,8.678 v8.678h-60.746c-4.793,0-8.678,3.885-8.678,8.678v95.458H17.356v-52.396c58.291-4.424,104.136-53.052,104.136-112.485 c0-4.793-3.885-8.678-8.678-8.678H17.356v-34.712h112.814c4.793,0,8.678-3.885,8.678-8.678v-60.746h8.678 c4.793,0,8.678-3.885,8.678-8.678s-3.885-8.678-8.678-8.678h-34.712c-4.793,0-8.678,3.885-8.678,8.678s3.885,8.678,8.678,8.678 h8.678v52.068H17.356V78.102h104.136v52.068h-8.678c-4.793,0-8.678,3.885-8.678,8.678c0,4.793,3.885,8.678,8.678,8.678h34.712 c4.793,0,8.678-3.885,8.678-8.678c0-4.793-3.885-8.678-8.678-8.678h-8.678V78.102h43.39v95.458c0,4.793,3.885,8.678,8.678,8.678 h34.712v8.669c0,4.793,3.885,8.678,8.678,8.678c4.793,0,8.678-3.885,8.678-8.678v-34.703c0-4.793-3.885-8.678-8.678-8.678 c-4.793,0-8.678,3.885-8.678,8.678v8.678h-26.034v-86.78h147.525v86.78h-34.712v-8.678c0-4.793-3.885-8.678-8.678-8.678 s-8.678,3.885-8.678,8.678v34.703c0,4.793,3.885,8.678,8.678,8.678s8.678-3.885,8.678-8.678v-8.669h43.39 c4.793,0,8.678-3.885,8.678-8.678V78.102h26.034v373.153c0,11.571,17.356,11.571,17.356,0c0-23.966,19.424-43.39,43.39-43.39 c23.966,0,43.39,19.424,43.39,43.39C494.644,475.446,475.446,494.644,451.775,494.644z"></path> </g> </g> </g></svg> -->
                  </template>
                  <template #heading>Dispozice</template>
                  <template #text>2+kk</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fal fa-building"></i></template>
                  <template #heading>Podlaží</template>
                  <template #text>3.&nbsp;patro</template>
                </InfoComp>
                <InfoComp>
                  <template #icon>
                    <i class="fa-light fa-ruler-combined"></i>
                    <!-- <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g transform="translate(1 1)"> <g> <g> <path d="M118.467,101.4c5.12,0,8.533-3.413,8.533-8.533V50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533H127 v-25.6C127,2.413,123.587-1,118.467-1s-8.533,3.413-8.533,8.533v85.333C109.933,97.987,113.347,101.4,118.467,101.4z"></path> <path d="M502.467,383h-25.6v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533V383h-42.667 c-5.12,0-8.533,3.413-8.533,8.533c0,5.12,3.413,8.533,8.533,8.533h85.333c5.12,0,8.533-3.413,8.533-8.533 C511,386.413,507.587,383,502.467,383z"></path> <path d="M92.867,459.8h-8.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S97.987,459.8,92.867,459.8z"></path> <path d="M135.533,459.8H127c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S140.653,459.8,135.533,459.8z"></path> <path d="M178.2,459.8h-8.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S183.32,459.8,178.2,459.8z"></path> <path d="M220.867,459.8h-8.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S225.987,459.8,220.867,459.8z"></path> <path d="M263.533,459.8H255c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S268.653,459.8,263.533,459.8z"></path> <path d="M306.2,459.8h-8.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S311.32,459.8,306.2,459.8z"></path> <path d="M348.867,459.8h-8.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S353.987,459.8,348.867,459.8z"></path> <path d="M391.533,459.8H383c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S396.653,459.8,391.533,459.8z"></path> <path d="M434.2,459.8h-8.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h8.533c5.12,0,8.533-3.413,8.533-8.533 S439.32,459.8,434.2,459.8z"></path> <path d="M502.467,459.8h-34.133c-5.12,0-8.533,3.413-8.533,8.533v34.133c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533 v-25.6h25.6c5.12,0,8.533-3.413,8.533-8.533S507.587,459.8,502.467,459.8z"></path> <path d="M425.667,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533h-8.533c-5.12,0-8.533,3.413-8.533,8.533 S420.547,50.2,425.667,50.2z"></path> <path d="M391.533,33.133H383c-5.12,0-8.533,3.413-8.533,8.533S377.88,50.2,383,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533 S396.653,33.133,391.533,33.133z"></path> <path d="M340.333,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533h-8.533c-5.12,0-8.533,3.413-8.533,8.533 S335.213,50.2,340.333,50.2z"></path> <path d="M297.667,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533h-8.533c-5.12,0-8.533,3.413-8.533,8.533 S292.547,50.2,297.667,50.2z"></path> <path d="M255,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533H255c-5.12,0-8.533,3.413-8.533,8.533 S249.88,50.2,255,50.2z"></path> <path d="M212.333,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533h-8.533c-5.12,0-8.533,3.413-8.533,8.533 S207.213,50.2,212.333,50.2z"></path> <path d="M169.667,50.2h8.533c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533h-8.533c-5.12,0-8.533,3.413-8.533,8.533 S164.547,50.2,169.667,50.2z"></path> <path d="M84.333,50.2c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533H75.8c-5.12,0-8.533,3.413-8.533,8.533 S70.68,50.2,75.8,50.2H84.333z"></path> <path d="M468.333,50.2h34.133c5.12,0,8.533-3.413,8.533-8.533s-3.413-8.533-8.533-8.533h-25.6v-25.6 c0-5.12-3.413-8.533-8.533-8.533S459.8,2.413,459.8,7.533v34.133C459.8,46.787,463.213,50.2,468.333,50.2z"></path> <path d="M41.667-1c-5.12,0-8.533,3.413-8.533,8.533v25.6h-25.6C2.413,33.133-1,36.547-1,41.667S2.413,50.2,7.533,50.2h34.133 c5.12,0,8.533-3.413,8.533-8.533V7.533C50.2,2.413,46.787-1,41.667-1z"></path> <path d="M41.667,75.8c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533v-8.533 C50.2,79.213,46.787,75.8,41.667,75.8z"></path> <path d="M41.667,118.467c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533V127 C50.2,121.88,46.787,118.467,41.667,118.467z"></path> <path d="M41.667,161.133c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533S50.2,183.32,50.2,178.2v-8.533 C50.2,164.547,46.787,161.133,41.667,161.133z"></path> <path d="M41.667,203.8c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533v-8.533 C50.2,207.213,46.787,203.8,41.667,203.8z"></path> <path d="M41.667,246.467c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533V255 C50.2,249.88,46.787,246.467,41.667,246.467z"></path> <path d="M41.667,289.133c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533S50.2,311.32,50.2,306.2v-8.533 C50.2,292.547,46.787,289.133,41.667,289.133z"></path> <path d="M41.667,331.8c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533v-8.533 C50.2,335.213,46.787,331.8,41.667,331.8z"></path> <path d="M41.667,374.467c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533s8.533-3.413,8.533-8.533V383 C50.2,377.88,46.787,374.467,41.667,374.467z"></path> <path d="M41.667,417.133c-5.12,0-8.533,3.413-8.533,8.533v8.533c0,5.12,3.413,8.533,8.533,8.533S50.2,439.32,50.2,434.2v-8.533 C50.2,420.547,46.787,417.133,41.667,417.133z"></path> <path d="M468.333,92.867c5.12,0,8.533-3.413,8.533-8.533V75.8c0-5.12-3.413-8.533-8.533-8.533S459.8,70.68,459.8,75.8v8.533 C459.8,89.453,463.213,92.867,468.333,92.867z"></path> <path d="M468.333,135.533c5.12,0,8.533-3.413,8.533-8.533v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533V127 C459.8,132.12,463.213,135.533,468.333,135.533z"></path> <path d="M468.333,178.2c5.12,0,8.533-3.413,8.533-8.533v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533v8.533 C459.8,174.787,463.213,178.2,468.333,178.2z"></path> <path d="M468.333,220.867c5.12,0,8.533-3.413,8.533-8.533V203.8c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533v8.533 C459.8,217.453,463.213,220.867,468.333,220.867z"></path> <path d="M468.333,263.533c5.12,0,8.533-3.413,8.533-8.533v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533V255 C459.8,260.12,463.213,263.533,468.333,263.533z"></path> <path d="M468.333,306.2c5.12,0,8.533-3.413,8.533-8.533v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533v8.533 C459.8,302.787,463.213,306.2,468.333,306.2z"></path> <path d="M468.333,348.867c5.12,0,8.533-3.413,8.533-8.533V331.8c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533v8.533 C459.8,345.453,463.213,348.867,468.333,348.867z"></path> <path d="M468.333,442.733c5.12,0,8.533-3.413,8.533-8.533v-8.533c0-5.12-3.413-8.533-8.533-8.533s-8.533,3.413-8.533,8.533v8.533 C459.8,439.32,463.213,442.733,468.333,442.733z"></path> <path d="M41.667,459.8H7.533c-5.12,0-8.533,3.413-8.533,8.533s3.413,8.533,8.533,8.533h25.6v25.6c0,5.12,3.413,8.533,8.533,8.533 s8.533-3.413,8.533-8.533v-34.133C50.2,463.213,46.787,459.8,41.667,459.8z"></path> <path d="M383,417.133V127c0-5.12-3.413-8.533-8.533-8.533H101.4c-5.12,0-8.533,3.413-8.533,8.533v290.133 c0,5.12,3.413,8.533,8.533,8.533h273.067C379.587,425.667,383,422.253,383,417.133z M365.933,408.6h-256V135.533h256V408.6z"></path> <path d="M122.487,313.634l24.14,24.14c1.707,1.707,3.413,2.56,5.973,2.56c2.56,0,4.267-0.853,5.973-2.56 c3.413-3.413,3.413-8.533,0-11.947l-11.093-11.093h124.587v56.32l-11.093-11.093c-3.413-3.413-8.533-3.413-11.947,0 s-3.413,8.533,0,11.947l24.14,24.14c1.395,2.509,4.034,4.02,7.433,4.02c3.399,0,6.038-1.511,7.433-4.02l24.14-24.14 c3.413-3.413,3.413-8.533,0-11.947c-3.413-3.413-8.533-3.413-11.947,0l-11.093,11.093v-56.32h39.253l-11.093,11.093 c-3.413,3.413-3.413,8.533,0,11.947c1.707,1.707,3.413,2.56,5.973,2.56s4.267-0.853,5.973-2.56l24.14-24.14 c2.509-1.395,4.02-4.034,4.02-7.433c0,0,0,0,0,0v0c0-3.399-1.511-6.038-4.02-7.434l-24.14-24.14 c-3.413-3.413-8.533-3.413-11.947,0s-3.413,8.533,0,11.947l11.093,11.093h-39.253V173.08l11.093,11.093 c1.707,1.707,3.413,2.56,5.973,2.56s4.267-0.853,5.973-2.56c3.413-3.413,3.413-8.533,0-11.947l-24.14-24.14 c-1.395-2.509-4.034-4.02-7.433-4.02s-6.038,1.511-7.433,4.02l-24.14,24.14c-3.413,3.413-3.413,8.533,0,11.947 s8.533,3.413,11.947,0l11.093-11.093v124.587H147.48l11.093-11.093c3.413-3.413,3.413-8.533,0-11.947s-8.533-3.413-11.947,0 l-24.14,24.14c-2.509,1.395-4.02,4.034-4.02,7.434S119.977,312.238,122.487,313.634z"></path> </g> </g> </g> </g></svg> -->
                  </template>
                  <template #heading>Plocha</template>
                  <template #text>174&nbsp;m²</template>
                </InfoComp>
              </div>
            </section>

            <hr class="tighten">
            
            <section id="e2">
              <h3>Základní informace</h3>
              <div class="info-comp-grid specs">
                <InfoComp>
                  <template #heading>Vnitřní užitná plocha</template>
                  <template #text>181.500&nbsp;Kč/m²</template>
                </InfoComp>
                <InfoComp>
                  <template #heading>Celková podlahová plocha</template>
                  <template #text>174&nbsp;m²</template>
                </InfoComp>
                <InfoComp>
                  <template #heading>Vnitřní užitná plocha</template>
                  <template #text>159&nbsp;m²</template>
                </InfoComp>
                <InfoComp>
                  <template #heading>Energetická náročnost budovy</template>
                  <template #text>B</template>
                </InfoComp>
                <InfoComp>
                  <template #heading>Orientace</template>
                  <template #text>SV, SJ</template>
                </InfoComp>
                <InfoComp>
                  <template #heading>Termín dokončení</template>
                  <template #text>DOKONČENO</template>
                </InfoComp>
              </div>
            </section>

            <section id="e3">
              <!-- <h3>Základní informace</h3> -->
              <div class="info-comp-grid specs-2">
                <!-- <PInfo>
                  <template #icon><i class="fa-light fa-circle-info"></i></template>
                  <template #heading>Celková podlahová plocha</template>
                  <template #text>174&nbsp;m²</template>
                </PInfo> -->
                <InfoComp>
                  <template #icon>
                    <svg fill="#20234c" height="200px" width="200px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 511.999 511.999" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M486.461,177.059H332.552V10.993c0-5.633-4.567-10.199-10.199-10.199H115.697c-5.633,0-10.199,4.566-10.199,10.199 v408.247c0,5.633,4.566,10.199,10.199,10.199h370.764v0c5.632,0,10.199-4.566,10.199-10.199V187.258 C496.66,181.625,492.093,177.059,486.461,177.059z M261.64,21.192h50.513v28.227H261.64V21.192z M125.896,21.192h115.346v28.226 H125.896V21.192z M177.422,409.041h-51.526V287.617h51.526V409.041z M312.154,409.041H197.821V287.617h114.333V409.041z M312.154,267.218H125.896v-197.4h186.258V267.218z M476.262,409.04h-143.71V197.458h143.71V409.04z"></path> </g> </g> <g> <g> <path d="M87.733,383.303c-3.983-3.982-10.441-3.982-14.425,0l-10.08,10.081V34.822l10.08,10.08 c1.992,1.992,4.602,2.987,7.212,2.987c2.61,0,5.221-0.995,7.212-2.987c3.983-3.983,3.983-10.441,0-14.425L60.241,2.986 c-3.983-3.982-10.441-3.982-14.425,0L18.326,30.478c-3.983,3.983-3.983,10.441,0,14.425c3.983,3.983,10.441,3.983,14.425,0 l10.08-10.081v358.563l-10.08-10.081c-3.983-3.982-10.441-3.982-14.425,0c-3.983,3.983-3.983,10.441,0,14.425l27.492,27.492 c1.992,1.992,4.602,2.987,7.212,2.987s5.221-0.995,7.212-2.987l27.492-27.493C91.716,393.745,91.716,387.287,87.733,383.303z"></path> </g> </g> <g> <g> <path d="M394.709,466.704H141.333l7.485-7.485c3.983-3.983,3.983-10.441,0-14.425c-3.983-3.983-10.441-3.983-14.425,0 l-24.896,24.896c-3.983,3.983-3.983,10.441,0,14.425l24.896,24.896c1.992,1.992,4.602,2.987,7.212,2.987s5.221-0.995,7.212-2.987 c3.983-3.983,3.983-10.441,0-14.425l-7.485-7.485h253.377c5.632,0,10.199-4.566,10.199-10.199S400.341,466.704,394.709,466.704z"></path> </g> </g> <g> <g> <path d="M436.526,466.704h-4.08c-5.632,0-10.199,4.566-10.199,10.199c0,5.633,4.567,10.199,10.199,10.199h4.08 c5.632,0,10.199-4.566,10.199-10.199C446.725,471.271,442.158,466.704,436.526,466.704z"></path> </g> </g> <g> <g> <path d="M493.235,469.692l-24.896-24.896c-3.984-3.983-10.44-3.983-14.425,0c-3.983,3.983-3.983,10.441,0,14.424l17.685,17.684 l-17.685,17.684c-3.983,3.983-3.983,10.441,0,14.424c1.992,1.992,4.602,2.987,7.212,2.987c2.61,0,5.22-0.996,7.212-2.987 l24.897-24.896c1.912-1.912,2.987-4.507,2.987-7.212S495.148,471.604,493.235,469.692z"></path> </g> </g> </g></svg>
                  </template>
                  <template #heading>Užitná plocha</template>
                  <template #text>
                    159&nbsp;m²
                    &nbsp;|&nbsp;
                    181.500&nbsp;Kč/m²
                  </template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-leaf"></i></template>
                  <!-- <template #heading>Energetická náročnost budovy</template> -->
                  <template #heading>Energetická třída</template>
                  <template #text>B</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-compass"></i></template>
                  <template #heading>Orientace</template>
                  <template #text>SV, SJ</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-calendar-check"></i></template>
                  <template #heading>Termín dokončení</template>
                  <template #text>Prosinec 2026</template>
                </InfoComp>
              </div>
            </section>

            <!-- <hr class="tighten"> -->

            <section id=e28>
              <h3>Místnosti (4+kk)</h3>
              <SpecsTable2 />
            </section>
            
            <section id="e4">
              <h3>Místnosti <small>(2+kk - table)</small></h3>
              <SpecsTable3 />
            </section>
            
            <section id=e31>
                <FancyBox class="pohledy">
                  <figure>
                    <figcaption>Půdorys podlaží</figcaption>
                    <img data-fancybox="pohledy-1" src="https://www.central-group.cz/Uloziste/85/85a7f7a6-d9b8-467c-9ac4-f8d25f8222af.png" alt="Půdorys podlaží">
                  </figure>
                  <figure>
                    <figcaption>Umístění patra v domě</figcaption>
                    <img data-fancybox="pohledy-1" src="https://www.central-group.cz/Uloziste/6b/6be248db-ea44-4f64-97e4-4d07e260a28b.gif" alt="Pohled na dům s vyznačením patra">
                  </figure>
                  <figure>
                    <figcaption>Situační plánek lokality</figcaption>
                    <img data-fancybox="pohledy-1" src="https://www.central-group.cz/Uloziste/7a/7a26b3e2-e74f-4431-b093-54e89cffb6f5.png" alt="Situační plánek lokality">
                  </figure>
                </FancyBox>
              <div>
              </div>
            </section>

            <hr class="tighten">

            <section id="e38">
              <div class="rooms-counter">
                <h3>Místnosti</h3>
                <h5 class="separator-underline">Vnitřní místnosti</h5>
                <ul class="bullet-points">
                  <li>
                      <span>Obývací pokoj a kuchyňský kout:</span> <strong>23,5&nbsp;m²</strong>
                  </li>
                  <li>
                      <span>Pokoj:</span> <strong>14&nbsp;m²</strong>
                  </li>
                  <li>
                      <span>Koupelna:</span> <strong>42,0&nbsp;m²</strong>
                  </li>
                  <li>
                      <span>Toaleta:</span> <strong>1,6&nbsp;m²</strong>
                  </li>
                  <li>
                      <span>Předsíň:</span> <strong>5,1&nbsp;m²</strong>
                  </li>
                </ul>
                <h5 class="separator-underline">Úložné prostory</h5>
                <ul class="bullet-points">
                  <li>
                      <span>Šatna:</span> <strong>4,5&nbsp;m²</strong>
                  </li>
                  <li>
                      <span>Komora:</span> <strong>3,9&nbsp;m²</strong>
                  </li>
                </ul>
                <h5 class="separator-underline">Vnější prostory</h5>
                <ul class="bullet-points">
                  <li>
                      <span>Terasa:</span> <strong>15,4&nbsp;m²</strong>
                  </li>
                  <li>
                      <span>Předzahrádka:</span> <strong>28&nbsp;m²</strong>
                  </li>
                </ul>
              </div>
            </section>


            <section id="e8">
              <h3>Ke stažení <small>(squares)</small></h3>
              <div class="cards-squared">
                <a href="#">
                  <InfoComp class="card">
                    <template #icon>
                      <i class="fal fa-file-pdf" data-v-inspector="src/views/HomeView.vue:568:59" data-v-b4e148ca=""></i>
                    </template>
                    <!-- <template #heading>Terasa</template> -->
                    <!-- <template #text>Stáhnout</template> -->
                    <template #text>Karta bytu</template>
                  </InfoComp>
                </a>
                <a href="#">
                  <InfoComp class="card">
                    <template #icon>
                      <i class="fal fa-file-pdf" data-v-inspector="src/views/HomeView.vue:568:59" data-v-b4e148ca=""></i>
                    </template>
                    <!-- <template #heading>Balkon</template> -->
                    <!-- <template #text>Stáhnout</template> -->
                    <template #text>Technický půdorys</template>
                  </InfoComp>
                </a>
                <a href="#">
                  <InfoComp class="card">
                    <template #icon>
                      <i class="fal fa-file-pdf" data-v-inspector="src/views/HomeView.vue:568:59" data-v-b4e148ca=""></i>
                    </template>
                    <!-- <template #heading>Předzahrádka</template> -->
                    <!-- <template #text>Stáhnout</template> -->
                    <template #text>Popis provedení</template>
                  </InfoComp>
                </a>
              </div>
            </section>

            <section id="e9">
              <h3>Ke stažení <small>(lines; variations)</small></h3>
              <div class="cards">
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #heading>Karta bytu</template>
                    <template #text><a href="#">Stáhnout</a></template>
                    <!-- <template #text><a href="#">Karta bytu</a></template> -->
                  </InfoComp>
                </div>
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <!-- <template #heading>Technický půdorys</template> -->
                    <!-- <template #text><a href="#">Stáhnout</a></template> -->
                    <template #text>Technický půdorys</template>
                  </InfoComp>
                  <div class="ta-r">
                    <a href="#" class="btn btn-gray">Stáhnout</a>
                  </div>
                </div>
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <!-- <template #heading>Technický půdorys</template> -->
                    <!-- <template #text><a href="#">Stáhnout</a></template> -->
                    <template #text><a href="#">Popis provedení</a></template>
                  </InfoComp>
                </div>
              </div>
            </section>

            <section id="e10">
              <h3>Ke stažení <small>(lines 2)</small></h3>
              <div class="cards">
                <a href="#" class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #text>Karta bytu</template>
                  </InfoComp>
                  <div class="ta-r">
                    <i class="fa-regular fa-arrow-down"></i>
                  </div>
                </a>
                <a href="#" class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #text>Technický půdorys</template>
                  </InfoComp>
                  <div class="ta-r">
                    <i class="fa-regular fa-arrow-down"></i>
                  </div>
                </a>
                <a href="#" class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #text>Popis provedení</template>
                  </InfoComp>
                  <div class="ta-r">
                    <i class="fa-regular fa-arrow-down"></i>
                  </div>
                </a>
              </div>
            </section>

            <section id="e11" class="mobile-only">
              <h3>Ke stažení</h3>
              <div class="card">
                <a href="#" class="card__row amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #text>Karta bytu</template>
                  </InfoComp>
                  <div class="ta-r">
                    <i class="fa-regular fa-arrow-down"></i>
                  </div>
                </a>
                <a href="#" class="card__row amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #text>Technický půdorys</template>
                  </InfoComp>
                  <div class="ta-r">
                    <i class="fa-regular fa-arrow-down"></i>
                  </div>
                </a>
                <a href="#" class="card__row amenity">
                  <InfoComp>
                    <template #icon>
                      <i class="fa-light fa-file-pdf"></i>
                    </template>
                    <template #text>Popis provedení</template>
                  </InfoComp>
                  <div class="ta-r">
                    <i class="fa-regular fa-arrow-down"></i>
                  </div>
                </a>
              </div>
            </section>

            <section id="e5">
              <h3>Příslušenství <small>(table)</small></h3>
              <div class="specs-table apart va-middle">
                <table>
                  <tbody>
                    <tr>
                      <td>
                        <InfoComp>
                          <template #icon>
                            <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 297 297" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <path d="M170.607,277.775h-12.495v-75.932h53.825c14.045,0,25.471-11.426,25.471-25.471c0-14.045-11.426-25.471-25.471-25.471 h-53.825V88.747h123.64c3.496,0,6.716-1.898,8.409-4.957c1.693-3.058,1.592-6.796-0.264-9.758 c-23.751-37.909-74.831-63.093-131.871-65.634C157.429,3.664,153.396,0,148.5,0s-8.929,3.664-9.527,8.398 C81.933,10.939,30.854,36.123,7.103,74.032c-1.856,2.962-1.957,6.7-0.264,9.758c1.693,3.059,4.913,4.957,8.409,4.957h123.64v62.155 H85.064c-14.045,0-25.471,11.426-25.471,25.471c0,14.045,11.426,25.471,25.471,25.471h53.825v75.932h-12.495 c-5.308,0-9.612,4.304-9.612,9.612s4.304,9.612,9.612,9.612h44.213c5.308,0,9.612-4.304,9.612-9.612 S175.915,277.775,170.607,277.775z M148.5,27.393c46.188,0,88.584,16.108,113.559,42.13H34.941 C59.916,43.501,102.312,27.393,148.5,27.393z M78.816,176.373c0-3.445,2.803-6.248,6.248-6.248h126.873 c3.445,0,6.248,2.803,6.248,6.248s-2.803,6.248-6.248,6.248H85.064C81.619,182.62,78.816,179.817,78.816,176.373z"></path> <path d="M95.727,221.865c-0.977-4.398-4.878-7.527-9.383-7.527H39.569V112.936c0-5.308-4.304-9.612-9.612-9.612 s-9.612,4.304-9.612,9.612v109.96L6.477,285.302c-1.152,5.181,2.116,10.316,7.298,11.467c0.702,0.156,1.403,0.231,2.094,0.231 c4.405,0,8.378-3.049,9.373-7.529l12.425-55.91h40.968l12.425,55.91c0.995,4.48,4.967,7.529,9.373,7.529 c0.691,0,1.392-0.075,2.094-0.231c5.182-1.152,8.45-6.286,7.298-11.467L95.727,221.865z"></path> <path d="M276.654,222.896v-109.96c0-5.308-4.304-9.612-9.612-9.612c-5.308,0-9.612,4.304-9.612,9.612v101.402h-46.776 c-4.504,0-8.405,3.128-9.383,7.527l-14.097,63.436c-1.152,5.181,2.116,10.316,7.298,11.467c0.702,0.156,1.403,0.231,2.094,0.231 c4.405,0,8.378-3.049,9.373-7.529l12.425-55.91h40.968l12.425,55.91c0.995,4.48,4.967,7.529,9.373,7.529 c0.691,0,1.392-0.075,2.094-0.231c5.182-1.152,8.45-6.286,7.298-11.467L276.654,222.896z"></path> </g> </g></svg>
                          </template>
                          <template #heading>Terasa</template>
                          <template #text></template>
                        </InfoComp>
                      </td>
                      <td></td>
                      <td><span>16,6&nbsp;m²</span></td>
                    </tr>
                    <tr>
                      <td>
                        <InfoComp>
                          <template #icon>
                            <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M473.043,413.088V267.13h22.261c9.22,0,16.696-7.475,16.696-16.696c0-9.22-7.475-16.696-16.696-16.696h-55.652V50.087 C439.652,22.469,417.183,0,389.565,0h-267.13C94.817,0,72.348,22.469,72.348,50.087v183.652H16.696 C7.475,233.739,0,241.214,0,250.435c0,9.22,7.475,16.696,16.696,16.696h22.261v145.958C16.68,418.165,0,438.121,0,461.913v33.391 C0,504.525,7.475,512,16.696,512h478.609c9.22,0,16.696-7.475,16.696-16.696v-33.391C512,438.121,495.32,418.165,473.043,413.088z M439.652,267.13v144.696h-33.391V267.13C418.344,267.13,427.569,267.13,439.652,267.13z M105.739,50.087 c0-9.206,7.49-16.696,16.696-16.696h267.13c9.206,0,16.696,7.49,16.696,16.696v183.652H372.87V83.478 c0-9.22-7.475-16.696-16.696-16.696H155.826c-9.22,0-16.696,7.475-16.696,16.696v150.261h-33.391V50.087z M272.696,233.739 V100.174h66.783v133.565H272.696z M306.087,267.13v144.696h-33.391V267.13H306.087z M339.478,267.13c12.083,0,21.308,0,33.391,0 v144.696h-33.391V267.13z M172.522,233.739V100.174h66.783v133.565H172.522z M239.304,267.13v144.696h-33.391V267.13H239.304z M172.522,267.13v144.696H139.13V267.13C151.214,267.13,160.439,267.13,172.522,267.13z M72.348,267.13 c12.083,0,21.308,0,33.391,0v144.696H72.348V267.13z M478.609,478.609H33.391v-16.696c0-9.206,7.49-16.696,16.696-16.696h411.826 c9.206,0,16.696,7.49,16.696,16.696V478.609z"></path> </g> </g> </g></svg>
                          </template>
                          <template #heading>Balkon</template>
                          <template #text></template>
                        </InfoComp>
                      </td>
                      <td></td>
                      <td><span>7,7&nbsp;m²</span></td>
                    </tr>
                    <tr>
                      <td>
                        <InfoComp>
                          <template #icon>
                            <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M501.289,256.353c5.915,0,10.711-4.797,10.711-10.711v-48.554c0-5.915-4.797-10.711-10.711-10.711h-25.064v-79.339 c0-2.084-0.608-4.125-1.751-5.869L446.41,58.324c-1.979-3.021-5.348-4.843-8.96-4.843s-6.982,1.821-8.96,4.843l-28.064,42.845 c-1.142,1.745-1.751,3.784-1.751,5.869v79.339h-44.132v-79.339c0-2.084-0.608-4.125-1.751-5.869l-28.064-42.845 c-1.979-3.022-5.348-4.843-8.96-4.843c-3.612,0-6.982,1.82-8.96,4.843l-28.064,42.845c-1.142,1.745-1.751,3.784-1.751,5.869 v79.339h-44.13v-79.339c0-2.084-0.608-4.125-1.751-5.869l-28.064-42.845c-1.979-3.021-5.348-4.843-8.96-4.843 s-6.982,1.821-8.96,4.843l-28.064,42.845c-1.143,1.744-1.751,3.783-1.751,5.869v79.339h-44.13v-79.339 c0-2.084-0.608-4.125-1.751-5.869L81.368,58.324c-1.979-3.021-5.348-4.843-8.96-4.843c-3.612,0-6.982,1.821-8.96,4.843 l-28.064,42.845c-3.241,4.949-1.857,11.588,3.091,14.83c4.949,3.239,11.589,1.856,14.83-3.091l19.103-29.166l17.352,26.491 v326.863H55.056V167.632c0-5.915-4.795-10.711-10.711-10.711c-5.916,0-10.711,4.797-10.711,10.711v18.745H10.711 C4.795,186.377,0,191.173,0,197.088v48.554c0,5.915,4.795,10.711,10.711,10.711h22.922v57.488H10.711 C4.795,313.841,0,318.638,0,324.552v48.554c0,5.915,4.795,10.711,10.711,10.711h22.922v63.989c0,5.915,4.795,10.711,10.711,10.711 h56.127c5.916,0,10.711-4.797,10.711-10.711v-63.989h44.13v63.989c0,5.915,4.795,10.711,10.711,10.711h56.127 c5.916,0,10.711-4.797,10.711-10.711v-63.989h44.131v63.989c0,5.915,4.797,10.711,10.711,10.711h56.127 c5.915,0,10.711-4.797,10.711-10.711v-63.989h44.131v63.989c0,5.915,4.797,10.711,10.711,10.711h56.127 c5.915,0,10.711-4.797,10.711-10.711v-63.989h25.064c5.915,0,10.711-4.797,10.711-10.711v-48.554 c0-5.915-4.797-10.711-10.711-10.711h-25.064v-57.488H501.289z M476.224,207.799h14.353v27.132h-14.353V207.799z M33.633,362.395 H21.423v-27.132h12.211V362.395z M33.633,234.931H21.423v-27.132h12.211V234.931z M155.314,362.395h-44.13v-27.132h44.13V362.395z M155.314,313.841h-44.13v-57.488h44.13V313.841z M155.314,234.931h-44.13v-27.132h44.13V234.931z M211.441,437.096h-34.705 V110.233l17.352-26.491l17.352,26.491V437.096z M276.994,362.395h-44.131v-27.132h44.131V362.395z M276.994,313.841h-44.131 v-57.488h44.131V313.841z M276.994,234.931h-44.131v-27.132h44.131V234.931z M333.121,437.096h-34.705V110.233l17.352-26.491 l17.352,26.491V437.096z M398.674,362.395h-44.131v-27.132h44.131V362.395z M398.674,313.841h-44.131v-57.488h44.131V313.841z M398.674,234.931h-44.131v-27.132h44.131V234.931z M420.097,437.096V110.233l17.352-26.491l17.351,26.491v326.863H420.097z M490.577,335.264v27.132h-14.353v-27.132H490.577z"></path> </g> </g> <g> <g> <path d="M44.345,124.872c-5.916,0-10.711,4.797-10.711,10.711v2.678c0,5.916,4.795,10.711,10.711,10.711 c5.916,0,10.711-4.797,10.711-10.711v-2.678C55.056,129.669,50.261,124.872,44.345,124.872z"></path> </g> </g> </g></svg>
                          </template>
                          <template #heading>Předzahrádka</template>
                          <template #text></template>
                        </InfoComp>
                      </td>
                      <td></td>
                      <td><span>33,7&nbsp;m²</span></td>
                    </tr>
                    <tr>
                      <td>
                        <InfoComp>
                          <template #icon>
                            <!-- <i class="fa-light fa-warehouse"></i> -->
                            <!-- https://www.svgrepo.com/svg/189864/warehouse-hangar -->
                            <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g transform="translate(1 1)"> <g> <g> <path d="M476.867-1H33.987C14.36-1-1,14.36-1,33.987v468.48c0,5.12,3.413,8.533,8.533,8.533H50.2h170.667h102.4h102.4H459.8 h42.667c5.12,0,8.533-3.413,8.533-8.533V33.987C511,14.36,495.64-1,476.867-1z M451.267,280.6H58.733v-17.067h392.533V280.6z M451.267,246.467H58.733V229.4h392.533V246.467z M58.733,297.667h392.533v17.067H58.733V297.667z M459.8,178.2H50.2v-34.133 h409.6V178.2z M451.267,195.267v17.067H58.733v-17.067H451.267z M92.867,476.867c0-9.387,7.68-17.067,17.067-17.067 S127,467.48,127,476.867s-7.68,17.067-17.067,17.067S92.867,486.253,92.867,476.867z M161.133,493.933 c-9.387,0-17.067-7.68-17.067-17.067s7.68-17.067,17.067-17.067c9.387,0,17.067,7.68,17.067,17.067 S170.52,493.933,161.133,493.933z M314.733,374.467H331.8v17.067h-17.067V374.467z M306.2,408.6h34.133 c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H357.4h-34.133h-34.133H280.6v-51.2h17.067v25.6 C297.667,405.187,301.08,408.6,306.2,408.6z M365.933,442.733h8.533H383V459.8h-17.067V442.733z M272.067,442.733h8.533V459.8 h-17.067v-17.067H272.067z M255,476.867h34.133c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H229.4v-51.2h17.067v25.6 C246.467,473.453,249.88,476.867,255,476.867z M331.8,493.933v-51.2h17.067v25.6c0,5.12,3.413,8.533,8.533,8.533h34.133 c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H331.8z M434.2,493.933V434.2c0-5.12-3.413-8.533-8.533-8.533h-34.133H383 v-59.733c0-5.12-3.413-8.533-8.533-8.533h-34.133H306.2h-34.133c-5.12,0-8.533,3.413-8.533,8.533v59.733H255h-34.133 c-5.12,0-8.533,3.413-8.533,8.533v59.733h-21.682c2.927-5.029,4.615-10.859,4.615-17.067c0-18.773-15.36-34.133-34.133-34.133 c-10.17,0-19.333,4.514-25.6,11.63c-6.267-7.117-15.43-11.63-25.6-11.63c-18.773,0-34.133,15.36-34.133,34.133 c0,6.208,1.688,12.037,4.615,17.067H58.733V331.8h392.533v162.133H434.2z M493.933,493.933h-25.6V323.267v-128 c5.12,0,8.533-3.413,8.533-8.533v-51.2c0-5.12-3.413-8.533-8.533-8.533H41.667c-5.12,0-8.533,3.413-8.533,8.533v51.2 c0,5.12,3.413,8.533,8.533,8.533v128v170.667h-25.6V33.987c0-10.24,7.68-17.92,17.92-17.92h442.027 c10.24,0,17.92,7.68,17.92,17.92V493.933z"></path> <path d="M374.467,33.133H135.533c-5.12,0-8.533,3.413-8.533,8.533V101.4c0,5.12,3.413,8.533,8.533,8.533h238.933 c5.12,0,8.533-3.413,8.533-8.533V41.667C383,36.547,379.587,33.133,374.467,33.133z M365.933,92.867H144.067V50.2h221.867V92.867 z"></path> </g> </g> </g> </g></svg>
                          </template>
                          <template #heading>Sklep</template>
                          <template #text><a href="#">PP2&nbsp;/&nbsp;S123</a></template>
                        </InfoComp>
                      </td>
                      <td></td>
                      <td>
                        <span>6,2&nbsp;m²</span>
                        <br>
                        <strong>275.670&nbsp;Kč</strong>
                      </td>
                    </tr>
                    <tr>
                      <td>
                        <InfoComp>
                          <template #icon>
                            <!-- <i class="fa-light fa-car"></i> -->
                            <svg width="24px" height="24px" viewBox="0 0 46 45" fill="none" xmlns="http://www.w3.org/2000/svg" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier" transform="scale(1.5)" transform-origin="50% 50%"> <path d="M32 29.6256H36V32.6256C36 33.1776 35.552 33.6256 35 33.6256H33C32.448 33.6256 32 33.1776 32 32.6256V29.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M10 29.6256H14V32.6256C14 33.1776 13.552 33.6256 13 33.6256H11C10.448 33.6256 10 33.1776 10 32.6256V29.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M14 19.6256H32C34.209 19.6256 36 21.4166 36 23.6256V28.6256C36 29.1776 35.552 29.6256 35 29.6256H11C10.448 29.6256 10 29.1776 10 28.6256V23.6256C10 21.4166 11.791 19.6256 14 19.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M32 23.6256C32.552 23.6256 33 24.0736 33 24.6256C33 25.1776 32.552 25.6256 32 25.6256C31.448 25.6256 31 25.1776 31 24.6256C31 24.0736 31.448 23.6256 32 23.6256Z" fill="#20234c"></path> <path d="M14 23.6256C14.552 23.6256 15 24.0736 15 24.6256C15 25.1776 14.552 25.6256 14 25.6256C13.448 25.6256 13 25.1776 13 24.6256C13 24.0736 13.448 23.6256 14 23.6256Z" fill="#20234c"></path> <path d="M15.693 11.6256H30.307C30.724 11.6256 31.097 11.8846 31.243 12.2746L34 19.6256H12L14.757 12.2746C14.903 11.8846 15.276 11.6256 15.693 11.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M9 16.6256H12V18.6256H9V16.6256Z" fill="#20234c"></path> <path d="M34 16.6256H37V18.6256H34V16.6256Z" fill="#20234c"></path> <path d="M17 24.6256H29" stroke="#20234c" stroke-width="2"></path> </g></svg>
                          </template>
                          <template #heading>Dvougarážové uzavřené stání</template>
                          <template #text><a href="#">PP2&nbsp;/&nbsp;2G100</a></template>
                        </InfoComp>
                      </td>
                      <td></td>
                      <td>
                        <strong>172.480&nbsp;Kč</strong>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </section>

            <!-- Amenities -->
            <section id="e6">
              <h3>Příslušenství</h3>
              <div class="cards-rows">
                <!-- Terasa -->
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 297 297" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <path d="M170.607,277.775h-12.495v-75.932h53.825c14.045,0,25.471-11.426,25.471-25.471c0-14.045-11.426-25.471-25.471-25.471 h-53.825V88.747h123.64c3.496,0,6.716-1.898,8.409-4.957c1.693-3.058,1.592-6.796-0.264-9.758 c-23.751-37.909-74.831-63.093-131.871-65.634C157.429,3.664,153.396,0,148.5,0s-8.929,3.664-9.527,8.398 C81.933,10.939,30.854,36.123,7.103,74.032c-1.856,2.962-1.957,6.7-0.264,9.758c1.693,3.059,4.913,4.957,8.409,4.957h123.64v62.155 H85.064c-14.045,0-25.471,11.426-25.471,25.471c0,14.045,11.426,25.471,25.471,25.471h53.825v75.932h-12.495 c-5.308,0-9.612,4.304-9.612,9.612s4.304,9.612,9.612,9.612h44.213c5.308,0,9.612-4.304,9.612-9.612 S175.915,277.775,170.607,277.775z M148.5,27.393c46.188,0,88.584,16.108,113.559,42.13H34.941 C59.916,43.501,102.312,27.393,148.5,27.393z M78.816,176.373c0-3.445,2.803-6.248,6.248-6.248h126.873 c3.445,0,6.248,2.803,6.248,6.248s-2.803,6.248-6.248,6.248H85.064C81.619,182.62,78.816,179.817,78.816,176.373z"></path> <path d="M95.727,221.865c-0.977-4.398-4.878-7.527-9.383-7.527H39.569V112.936c0-5.308-4.304-9.612-9.612-9.612 s-9.612,4.304-9.612,9.612v109.96L6.477,285.302c-1.152,5.181,2.116,10.316,7.298,11.467c0.702,0.156,1.403,0.231,2.094,0.231 c4.405,0,8.378-3.049,9.373-7.529l12.425-55.91h40.968l12.425,55.91c0.995,4.48,4.967,7.529,9.373,7.529 c0.691,0,1.392-0.075,2.094-0.231c5.182-1.152,8.45-6.286,7.298-11.467L95.727,221.865z"></path> <path d="M276.654,222.896v-109.96c0-5.308-4.304-9.612-9.612-9.612c-5.308,0-9.612,4.304-9.612,9.612v101.402h-46.776 c-4.504,0-8.405,3.128-9.383,7.527l-14.097,63.436c-1.152,5.181,2.116,10.316,7.298,11.467c0.702,0.156,1.403,0.231,2.094,0.231 c4.405,0,8.378-3.049,9.373-7.529l12.425-55.91h40.968l12.425,55.91c0.995,4.48,4.967,7.529,9.373,7.529 c0.691,0,1.392-0.075,2.094-0.231c5.182-1.152,8.45-6.286,7.298-11.467L276.654,222.896z"></path> </g> </g></svg>
                    </template>
                    <template #heading>Terasa</template>
                    <template #text></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>16,6&nbsp;m²</span>
                  </div>
                </div>
                <!-- Balkon -->
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M473.043,413.088V267.13h22.261c9.22,0,16.696-7.475,16.696-16.696c0-9.22-7.475-16.696-16.696-16.696h-55.652V50.087 C439.652,22.469,417.183,0,389.565,0h-267.13C94.817,0,72.348,22.469,72.348,50.087v183.652H16.696 C7.475,233.739,0,241.214,0,250.435c0,9.22,7.475,16.696,16.696,16.696h22.261v145.958C16.68,418.165,0,438.121,0,461.913v33.391 C0,504.525,7.475,512,16.696,512h478.609c9.22,0,16.696-7.475,16.696-16.696v-33.391C512,438.121,495.32,418.165,473.043,413.088z M439.652,267.13v144.696h-33.391V267.13C418.344,267.13,427.569,267.13,439.652,267.13z M105.739,50.087 c0-9.206,7.49-16.696,16.696-16.696h267.13c9.206,0,16.696,7.49,16.696,16.696v183.652H372.87V83.478 c0-9.22-7.475-16.696-16.696-16.696H155.826c-9.22,0-16.696,7.475-16.696,16.696v150.261h-33.391V50.087z M272.696,233.739 V100.174h66.783v133.565H272.696z M306.087,267.13v144.696h-33.391V267.13H306.087z M339.478,267.13c12.083,0,21.308,0,33.391,0 v144.696h-33.391V267.13z M172.522,233.739V100.174h66.783v133.565H172.522z M239.304,267.13v144.696h-33.391V267.13H239.304z M172.522,267.13v144.696H139.13V267.13C151.214,267.13,160.439,267.13,172.522,267.13z M72.348,267.13 c12.083,0,21.308,0,33.391,0v144.696H72.348V267.13z M478.609,478.609H33.391v-16.696c0-9.206,7.49-16.696,16.696-16.696h411.826 c9.206,0,16.696,7.49,16.696,16.696V478.609z"></path> </g> </g> </g></svg>
                    </template>
                    <template #heading>Balkon</template>
                    <template #text></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>7,7&nbsp;m²</span>
                  </div>
                </div>
                <!-- Předzahrádka -->
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M501.289,256.353c5.915,0,10.711-4.797,10.711-10.711v-48.554c0-5.915-4.797-10.711-10.711-10.711h-25.064v-79.339 c0-2.084-0.608-4.125-1.751-5.869L446.41,58.324c-1.979-3.021-5.348-4.843-8.96-4.843s-6.982,1.821-8.96,4.843l-28.064,42.845 c-1.142,1.745-1.751,3.784-1.751,5.869v79.339h-44.132v-79.339c0-2.084-0.608-4.125-1.751-5.869l-28.064-42.845 c-1.979-3.022-5.348-4.843-8.96-4.843c-3.612,0-6.982,1.82-8.96,4.843l-28.064,42.845c-1.142,1.745-1.751,3.784-1.751,5.869 v79.339h-44.13v-79.339c0-2.084-0.608-4.125-1.751-5.869l-28.064-42.845c-1.979-3.021-5.348-4.843-8.96-4.843 s-6.982,1.821-8.96,4.843l-28.064,42.845c-1.143,1.744-1.751,3.783-1.751,5.869v79.339h-44.13v-79.339 c0-2.084-0.608-4.125-1.751-5.869L81.368,58.324c-1.979-3.021-5.348-4.843-8.96-4.843c-3.612,0-6.982,1.821-8.96,4.843 l-28.064,42.845c-3.241,4.949-1.857,11.588,3.091,14.83c4.949,3.239,11.589,1.856,14.83-3.091l19.103-29.166l17.352,26.491 v326.863H55.056V167.632c0-5.915-4.795-10.711-10.711-10.711c-5.916,0-10.711,4.797-10.711,10.711v18.745H10.711 C4.795,186.377,0,191.173,0,197.088v48.554c0,5.915,4.795,10.711,10.711,10.711h22.922v57.488H10.711 C4.795,313.841,0,318.638,0,324.552v48.554c0,5.915,4.795,10.711,10.711,10.711h22.922v63.989c0,5.915,4.795,10.711,10.711,10.711 h56.127c5.916,0,10.711-4.797,10.711-10.711v-63.989h44.13v63.989c0,5.915,4.795,10.711,10.711,10.711h56.127 c5.916,0,10.711-4.797,10.711-10.711v-63.989h44.131v63.989c0,5.915,4.797,10.711,10.711,10.711h56.127 c5.915,0,10.711-4.797,10.711-10.711v-63.989h44.131v63.989c0,5.915,4.797,10.711,10.711,10.711h56.127 c5.915,0,10.711-4.797,10.711-10.711v-63.989h25.064c5.915,0,10.711-4.797,10.711-10.711v-48.554 c0-5.915-4.797-10.711-10.711-10.711h-25.064v-57.488H501.289z M476.224,207.799h14.353v27.132h-14.353V207.799z M33.633,362.395 H21.423v-27.132h12.211V362.395z M33.633,234.931H21.423v-27.132h12.211V234.931z M155.314,362.395h-44.13v-27.132h44.13V362.395z M155.314,313.841h-44.13v-57.488h44.13V313.841z M155.314,234.931h-44.13v-27.132h44.13V234.931z M211.441,437.096h-34.705 V110.233l17.352-26.491l17.352,26.491V437.096z M276.994,362.395h-44.131v-27.132h44.131V362.395z M276.994,313.841h-44.131 v-57.488h44.131V313.841z M276.994,234.931h-44.131v-27.132h44.131V234.931z M333.121,437.096h-34.705V110.233l17.352-26.491 l17.352,26.491V437.096z M398.674,362.395h-44.131v-27.132h44.131V362.395z M398.674,313.841h-44.131v-57.488h44.131V313.841z M398.674,234.931h-44.131v-27.132h44.131V234.931z M420.097,437.096V110.233l17.352-26.491l17.351,26.491v326.863H420.097z M490.577,335.264v27.132h-14.353v-27.132H490.577z"></path> </g> </g> <g> <g> <path d="M44.345,124.872c-5.916,0-10.711,4.797-10.711,10.711v2.678c0,5.916,4.795,10.711,10.711,10.711 c5.916,0,10.711-4.797,10.711-10.711v-2.678C55.056,129.669,50.261,124.872,44.345,124.872z"></path> </g> </g> </g></svg>
                    </template>
                    <template #heading>Předzahrádka</template>
                    <template #text></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>33,7&nbsp;m²</span>
                  </div>
                </div>
                <!-- Sklep -->
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <!-- <i class="fa-light fa-warehouse"></i> -->
                      <!-- https://www.svgrepo.com/svg/189864/warehouse-hangar -->
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g transform="translate(1 1)"> <g> <g> <path d="M476.867-1H33.987C14.36-1-1,14.36-1,33.987v468.48c0,5.12,3.413,8.533,8.533,8.533H50.2h170.667h102.4h102.4H459.8 h42.667c5.12,0,8.533-3.413,8.533-8.533V33.987C511,14.36,495.64-1,476.867-1z M451.267,280.6H58.733v-17.067h392.533V280.6z M451.267,246.467H58.733V229.4h392.533V246.467z M58.733,297.667h392.533v17.067H58.733V297.667z M459.8,178.2H50.2v-34.133 h409.6V178.2z M451.267,195.267v17.067H58.733v-17.067H451.267z M92.867,476.867c0-9.387,7.68-17.067,17.067-17.067 S127,467.48,127,476.867s-7.68,17.067-17.067,17.067S92.867,486.253,92.867,476.867z M161.133,493.933 c-9.387,0-17.067-7.68-17.067-17.067s7.68-17.067,17.067-17.067c9.387,0,17.067,7.68,17.067,17.067 S170.52,493.933,161.133,493.933z M314.733,374.467H331.8v17.067h-17.067V374.467z M306.2,408.6h34.133 c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H357.4h-34.133h-34.133H280.6v-51.2h17.067v25.6 C297.667,405.187,301.08,408.6,306.2,408.6z M365.933,442.733h8.533H383V459.8h-17.067V442.733z M272.067,442.733h8.533V459.8 h-17.067v-17.067H272.067z M255,476.867h34.133c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H229.4v-51.2h17.067v25.6 C246.467,473.453,249.88,476.867,255,476.867z M331.8,493.933v-51.2h17.067v25.6c0,5.12,3.413,8.533,8.533,8.533h34.133 c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H331.8z M434.2,493.933V434.2c0-5.12-3.413-8.533-8.533-8.533h-34.133H383 v-59.733c0-5.12-3.413-8.533-8.533-8.533h-34.133H306.2h-34.133c-5.12,0-8.533,3.413-8.533,8.533v59.733H255h-34.133 c-5.12,0-8.533,3.413-8.533,8.533v59.733h-21.682c2.927-5.029,4.615-10.859,4.615-17.067c0-18.773-15.36-34.133-34.133-34.133 c-10.17,0-19.333,4.514-25.6,11.63c-6.267-7.117-15.43-11.63-25.6-11.63c-18.773,0-34.133,15.36-34.133,34.133 c0,6.208,1.688,12.037,4.615,17.067H58.733V331.8h392.533v162.133H434.2z M493.933,493.933h-25.6V323.267v-128 c5.12,0,8.533-3.413,8.533-8.533v-51.2c0-5.12-3.413-8.533-8.533-8.533H41.667c-5.12,0-8.533,3.413-8.533,8.533v51.2 c0,5.12,3.413,8.533,8.533,8.533v128v170.667h-25.6V33.987c0-10.24,7.68-17.92,17.92-17.92h442.027 c10.24,0,17.92,7.68,17.92,17.92V493.933z"></path> <path d="M374.467,33.133H135.533c-5.12,0-8.533,3.413-8.533,8.533V101.4c0,5.12,3.413,8.533,8.533,8.533h238.933 c5.12,0,8.533-3.413,8.533-8.533V41.667C383,36.547,379.587,33.133,374.467,33.133z M365.933,92.867H144.067V50.2h221.867V92.867 z"></path> </g> </g> </g> </g></svg>
                    </template>
                    <template #heading>Sklep</template>
                    <template #text><a href="#">PP2&nbsp;/&nbsp;S123</a></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>6,2&nbsp;m²</span>
                    <br>
                    <strong>275.670&nbsp;Kč</strong>
                  </div>
                </div>
                <!-- Dvougarážové uzavřené stání -->
                <div class="card amenity">
                  <InfoComp>
                    <template #icon>
                      <!-- <i class="fa-light fa-car"></i> -->
                      <svg width="24px" height="24px" viewBox="0 0 46 45" fill="none" xmlns="http://www.w3.org/2000/svg" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier" transform="scale(1.5)" transform-origin="50% 50%"> <path d="M32 29.6256H36V32.6256C36 33.1776 35.552 33.6256 35 33.6256H33C32.448 33.6256 32 33.1776 32 32.6256V29.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M10 29.6256H14V32.6256C14 33.1776 13.552 33.6256 13 33.6256H11C10.448 33.6256 10 33.1776 10 32.6256V29.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M14 19.6256H32C34.209 19.6256 36 21.4166 36 23.6256V28.6256C36 29.1776 35.552 29.6256 35 29.6256H11C10.448 29.6256 10 29.1776 10 28.6256V23.6256C10 21.4166 11.791 19.6256 14 19.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M32 23.6256C32.552 23.6256 33 24.0736 33 24.6256C33 25.1776 32.552 25.6256 32 25.6256C31.448 25.6256 31 25.1776 31 24.6256C31 24.0736 31.448 23.6256 32 23.6256Z" fill="#20234c"></path> <path d="M14 23.6256C14.552 23.6256 15 24.0736 15 24.6256C15 25.1776 14.552 25.6256 14 25.6256C13.448 25.6256 13 25.1776 13 24.6256C13 24.0736 13.448 23.6256 14 23.6256Z" fill="#20234c"></path> <path d="M15.693 11.6256H30.307C30.724 11.6256 31.097 11.8846 31.243 12.2746L34 19.6256H12L14.757 12.2746C14.903 11.8846 15.276 11.6256 15.693 11.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M9 16.6256H12V18.6256H9V16.6256Z" fill="#20234c"></path> <path d="M34 16.6256H37V18.6256H34V16.6256Z" fill="#20234c"></path> <path d="M17 24.6256H29" stroke="#20234c" stroke-width="2"></path> </g></svg>
                    </template>
                    <template #heading>Dvougarážové uzavřené stání</template>
                    <template #text><a href="#">PP2&nbsp;/&nbsp;2G100</a></template>
                  </InfoComp>
                  <div class="ta-r">
                    <strong>172.480&nbsp;Kč</strong>
                  </div>
                </div>
              </div>
            </section>

            <!-- Amenities -->
            <section id="e32">
              <h3>Příslušenství</h3>
              <div class="info-comp-grid sm-wrap">
                <!-- Terasa -->
                <div class="amenity">
                  <InfoComp>
                    <template #icon>
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 297 297" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <path d="M170.607,277.775h-12.495v-75.932h53.825c14.045,0,25.471-11.426,25.471-25.471c0-14.045-11.426-25.471-25.471-25.471 h-53.825V88.747h123.64c3.496,0,6.716-1.898,8.409-4.957c1.693-3.058,1.592-6.796-0.264-9.758 c-23.751-37.909-74.831-63.093-131.871-65.634C157.429,3.664,153.396,0,148.5,0s-8.929,3.664-9.527,8.398 C81.933,10.939,30.854,36.123,7.103,74.032c-1.856,2.962-1.957,6.7-0.264,9.758c1.693,3.059,4.913,4.957,8.409,4.957h123.64v62.155 H85.064c-14.045,0-25.471,11.426-25.471,25.471c0,14.045,11.426,25.471,25.471,25.471h53.825v75.932h-12.495 c-5.308,0-9.612,4.304-9.612,9.612s4.304,9.612,9.612,9.612h44.213c5.308,0,9.612-4.304,9.612-9.612 S175.915,277.775,170.607,277.775z M148.5,27.393c46.188,0,88.584,16.108,113.559,42.13H34.941 C59.916,43.501,102.312,27.393,148.5,27.393z M78.816,176.373c0-3.445,2.803-6.248,6.248-6.248h126.873 c3.445,0,6.248,2.803,6.248,6.248s-2.803,6.248-6.248,6.248H85.064C81.619,182.62,78.816,179.817,78.816,176.373z"></path> <path d="M95.727,221.865c-0.977-4.398-4.878-7.527-9.383-7.527H39.569V112.936c0-5.308-4.304-9.612-9.612-9.612 s-9.612,4.304-9.612,9.612v109.96L6.477,285.302c-1.152,5.181,2.116,10.316,7.298,11.467c0.702,0.156,1.403,0.231,2.094,0.231 c4.405,0,8.378-3.049,9.373-7.529l12.425-55.91h40.968l12.425,55.91c0.995,4.48,4.967,7.529,9.373,7.529 c0.691,0,1.392-0.075,2.094-0.231c5.182-1.152,8.45-6.286,7.298-11.467L95.727,221.865z"></path> <path d="M276.654,222.896v-109.96c0-5.308-4.304-9.612-9.612-9.612c-5.308,0-9.612,4.304-9.612,9.612v101.402h-46.776 c-4.504,0-8.405,3.128-9.383,7.527l-14.097,63.436c-1.152,5.181,2.116,10.316,7.298,11.467c0.702,0.156,1.403,0.231,2.094,0.231 c4.405,0,8.378-3.049,9.373-7.529l12.425-55.91h40.968l12.425,55.91c0.995,4.48,4.967,7.529,9.373,7.529 c0.691,0,1.392-0.075,2.094-0.231c5.182-1.152,8.45-6.286,7.298-11.467L276.654,222.896z"></path> </g> </g></svg>
                    </template>
                    <template #heading>Terasa</template>
                    <template #text></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>16,6&nbsp;m²</span>
                  </div>
                </div>
                <!-- Balkon -->
                <div class="amenity">
                  <InfoComp>
                    <template #icon>
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M473.043,413.088V267.13h22.261c9.22,0,16.696-7.475,16.696-16.696c0-9.22-7.475-16.696-16.696-16.696h-55.652V50.087 C439.652,22.469,417.183,0,389.565,0h-267.13C94.817,0,72.348,22.469,72.348,50.087v183.652H16.696 C7.475,233.739,0,241.214,0,250.435c0,9.22,7.475,16.696,16.696,16.696h22.261v145.958C16.68,418.165,0,438.121,0,461.913v33.391 C0,504.525,7.475,512,16.696,512h478.609c9.22,0,16.696-7.475,16.696-16.696v-33.391C512,438.121,495.32,418.165,473.043,413.088z M439.652,267.13v144.696h-33.391V267.13C418.344,267.13,427.569,267.13,439.652,267.13z M105.739,50.087 c0-9.206,7.49-16.696,16.696-16.696h267.13c9.206,0,16.696,7.49,16.696,16.696v183.652H372.87V83.478 c0-9.22-7.475-16.696-16.696-16.696H155.826c-9.22,0-16.696,7.475-16.696,16.696v150.261h-33.391V50.087z M272.696,233.739 V100.174h66.783v133.565H272.696z M306.087,267.13v144.696h-33.391V267.13H306.087z M339.478,267.13c12.083,0,21.308,0,33.391,0 v144.696h-33.391V267.13z M172.522,233.739V100.174h66.783v133.565H172.522z M239.304,267.13v144.696h-33.391V267.13H239.304z M172.522,267.13v144.696H139.13V267.13C151.214,267.13,160.439,267.13,172.522,267.13z M72.348,267.13 c12.083,0,21.308,0,33.391,0v144.696H72.348V267.13z M478.609,478.609H33.391v-16.696c0-9.206,7.49-16.696,16.696-16.696h411.826 c9.206,0,16.696,7.49,16.696,16.696V478.609z"></path> </g> </g> </g></svg>
                    </template>
                    <template #heading>Balkon</template>
                    <template #text></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>7,7&nbsp;m²</span>
                  </div>
                </div>
                <!-- Předzahrádka -->
                <div class="amenity">
                  <InfoComp>
                    <template #icon>
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g> <g> <path d="M501.289,256.353c5.915,0,10.711-4.797,10.711-10.711v-48.554c0-5.915-4.797-10.711-10.711-10.711h-25.064v-79.339 c0-2.084-0.608-4.125-1.751-5.869L446.41,58.324c-1.979-3.021-5.348-4.843-8.96-4.843s-6.982,1.821-8.96,4.843l-28.064,42.845 c-1.142,1.745-1.751,3.784-1.751,5.869v79.339h-44.132v-79.339c0-2.084-0.608-4.125-1.751-5.869l-28.064-42.845 c-1.979-3.022-5.348-4.843-8.96-4.843c-3.612,0-6.982,1.82-8.96,4.843l-28.064,42.845c-1.142,1.745-1.751,3.784-1.751,5.869 v79.339h-44.13v-79.339c0-2.084-0.608-4.125-1.751-5.869l-28.064-42.845c-1.979-3.021-5.348-4.843-8.96-4.843 s-6.982,1.821-8.96,4.843l-28.064,42.845c-1.143,1.744-1.751,3.783-1.751,5.869v79.339h-44.13v-79.339 c0-2.084-0.608-4.125-1.751-5.869L81.368,58.324c-1.979-3.021-5.348-4.843-8.96-4.843c-3.612,0-6.982,1.821-8.96,4.843 l-28.064,42.845c-3.241,4.949-1.857,11.588,3.091,14.83c4.949,3.239,11.589,1.856,14.83-3.091l19.103-29.166l17.352,26.491 v326.863H55.056V167.632c0-5.915-4.795-10.711-10.711-10.711c-5.916,0-10.711,4.797-10.711,10.711v18.745H10.711 C4.795,186.377,0,191.173,0,197.088v48.554c0,5.915,4.795,10.711,10.711,10.711h22.922v57.488H10.711 C4.795,313.841,0,318.638,0,324.552v48.554c0,5.915,4.795,10.711,10.711,10.711h22.922v63.989c0,5.915,4.795,10.711,10.711,10.711 h56.127c5.916,0,10.711-4.797,10.711-10.711v-63.989h44.13v63.989c0,5.915,4.795,10.711,10.711,10.711h56.127 c5.916,0,10.711-4.797,10.711-10.711v-63.989h44.131v63.989c0,5.915,4.797,10.711,10.711,10.711h56.127 c5.915,0,10.711-4.797,10.711-10.711v-63.989h44.131v63.989c0,5.915,4.797,10.711,10.711,10.711h56.127 c5.915,0,10.711-4.797,10.711-10.711v-63.989h25.064c5.915,0,10.711-4.797,10.711-10.711v-48.554 c0-5.915-4.797-10.711-10.711-10.711h-25.064v-57.488H501.289z M476.224,207.799h14.353v27.132h-14.353V207.799z M33.633,362.395 H21.423v-27.132h12.211V362.395z M33.633,234.931H21.423v-27.132h12.211V234.931z M155.314,362.395h-44.13v-27.132h44.13V362.395z M155.314,313.841h-44.13v-57.488h44.13V313.841z M155.314,234.931h-44.13v-27.132h44.13V234.931z M211.441,437.096h-34.705 V110.233l17.352-26.491l17.352,26.491V437.096z M276.994,362.395h-44.131v-27.132h44.131V362.395z M276.994,313.841h-44.131 v-57.488h44.131V313.841z M276.994,234.931h-44.131v-27.132h44.131V234.931z M333.121,437.096h-34.705V110.233l17.352-26.491 l17.352,26.491V437.096z M398.674,362.395h-44.131v-27.132h44.131V362.395z M398.674,313.841h-44.131v-57.488h44.131V313.841z M398.674,234.931h-44.131v-27.132h44.131V234.931z M420.097,437.096V110.233l17.352-26.491l17.351,26.491v326.863H420.097z M490.577,335.264v27.132h-14.353v-27.132H490.577z"></path> </g> </g> <g> <g> <path d="M44.345,124.872c-5.916,0-10.711,4.797-10.711,10.711v2.678c0,5.916,4.795,10.711,10.711,10.711 c5.916,0,10.711-4.797,10.711-10.711v-2.678C55.056,129.669,50.261,124.872,44.345,124.872z"></path> </g> </g> </g></svg>
                    </template>
                    <template #heading>Předzahrádka</template>
                    <template #text></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>33,7&nbsp;m²</span>
                  </div>
                </div>
                <!-- Sklep -->
                <div class="amenity">
                  <InfoComp>
                    <template #icon>
                      <!-- <i class="fa-light fa-warehouse"></i> -->
                      <!-- https://www.svgrepo.com/svg/189864/warehouse-hangar -->
                      <svg fill="#20234c" height="24px" width="24px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 512 512" xml:space="preserve" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g transform="translate(1 1)"> <g> <g> <path d="M476.867-1H33.987C14.36-1-1,14.36-1,33.987v468.48c0,5.12,3.413,8.533,8.533,8.533H50.2h170.667h102.4h102.4H459.8 h42.667c5.12,0,8.533-3.413,8.533-8.533V33.987C511,14.36,495.64-1,476.867-1z M451.267,280.6H58.733v-17.067h392.533V280.6z M451.267,246.467H58.733V229.4h392.533V246.467z M58.733,297.667h392.533v17.067H58.733V297.667z M459.8,178.2H50.2v-34.133 h409.6V178.2z M451.267,195.267v17.067H58.733v-17.067H451.267z M92.867,476.867c0-9.387,7.68-17.067,17.067-17.067 S127,467.48,127,476.867s-7.68,17.067-17.067,17.067S92.867,486.253,92.867,476.867z M161.133,493.933 c-9.387,0-17.067-7.68-17.067-17.067s7.68-17.067,17.067-17.067c9.387,0,17.067,7.68,17.067,17.067 S170.52,493.933,161.133,493.933z M314.733,374.467H331.8v17.067h-17.067V374.467z M306.2,408.6h34.133 c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H357.4h-34.133h-34.133H280.6v-51.2h17.067v25.6 C297.667,405.187,301.08,408.6,306.2,408.6z M365.933,442.733h8.533H383V459.8h-17.067V442.733z M272.067,442.733h8.533V459.8 h-17.067v-17.067H272.067z M255,476.867h34.133c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H229.4v-51.2h17.067v25.6 C246.467,473.453,249.88,476.867,255,476.867z M331.8,493.933v-51.2h17.067v25.6c0,5.12,3.413,8.533,8.533,8.533h34.133 c5.12,0,8.533-3.413,8.533-8.533v-25.6h17.067v51.2H331.8z M434.2,493.933V434.2c0-5.12-3.413-8.533-8.533-8.533h-34.133H383 v-59.733c0-5.12-3.413-8.533-8.533-8.533h-34.133H306.2h-34.133c-5.12,0-8.533,3.413-8.533,8.533v59.733H255h-34.133 c-5.12,0-8.533,3.413-8.533,8.533v59.733h-21.682c2.927-5.029,4.615-10.859,4.615-17.067c0-18.773-15.36-34.133-34.133-34.133 c-10.17,0-19.333,4.514-25.6,11.63c-6.267-7.117-15.43-11.63-25.6-11.63c-18.773,0-34.133,15.36-34.133,34.133 c0,6.208,1.688,12.037,4.615,17.067H58.733V331.8h392.533v162.133H434.2z M493.933,493.933h-25.6V323.267v-128 c5.12,0,8.533-3.413,8.533-8.533v-51.2c0-5.12-3.413-8.533-8.533-8.533H41.667c-5.12,0-8.533,3.413-8.533,8.533v51.2 c0,5.12,3.413,8.533,8.533,8.533v128v170.667h-25.6V33.987c0-10.24,7.68-17.92,17.92-17.92h442.027 c10.24,0,17.92,7.68,17.92,17.92V493.933z"></path> <path d="M374.467,33.133H135.533c-5.12,0-8.533,3.413-8.533,8.533V101.4c0,5.12,3.413,8.533,8.533,8.533h238.933 c5.12,0,8.533-3.413,8.533-8.533V41.667C383,36.547,379.587,33.133,374.467,33.133z M365.933,92.867H144.067V50.2h221.867V92.867 z"></path> </g> </g> </g> </g></svg>
                    </template>
                    <template #heading>Sklep</template>
                    <template #text><a href="#">PP2&nbsp;/&nbsp;S123</a></template>
                  </InfoComp>
                  <div class="ta-r">
                    <span>6,2&nbsp;m²</span>
                    <br>
                    <strong>275.670&nbsp;Kč</strong>
                  </div>
                </div>
                <!-- Dvougarážové uzavřené stání -->
                <div class="amenity">
                  <InfoComp>
                    <template #icon>
                      <!-- <i class="fa-light fa-car"></i> -->
                      <svg width="24px" height="24px" viewBox="0 0 46 45" fill="none" xmlns="http://www.w3.org/2000/svg" stroke="#20234c"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier" transform="scale(1.5)" transform-origin="50% 50%"> <path d="M32 29.6256H36V32.6256C36 33.1776 35.552 33.6256 35 33.6256H33C32.448 33.6256 32 33.1776 32 32.6256V29.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M10 29.6256H14V32.6256C14 33.1776 13.552 33.6256 13 33.6256H11C10.448 33.6256 10 33.1776 10 32.6256V29.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M14 19.6256H32C34.209 19.6256 36 21.4166 36 23.6256V28.6256C36 29.1776 35.552 29.6256 35 29.6256H11C10.448 29.6256 10 29.1776 10 28.6256V23.6256C10 21.4166 11.791 19.6256 14 19.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M32 23.6256C32.552 23.6256 33 24.0736 33 24.6256C33 25.1776 32.552 25.6256 32 25.6256C31.448 25.6256 31 25.1776 31 24.6256C31 24.0736 31.448 23.6256 32 23.6256Z" fill="#20234c"></path> <path d="M14 23.6256C14.552 23.6256 15 24.0736 15 24.6256C15 25.1776 14.552 25.6256 14 25.6256C13.448 25.6256 13 25.1776 13 24.6256C13 24.0736 13.448 23.6256 14 23.6256Z" fill="#20234c"></path> <path d="M15.693 11.6256H30.307C30.724 11.6256 31.097 11.8846 31.243 12.2746L34 19.6256H12L14.757 12.2746C14.903 11.8846 15.276 11.6256 15.693 11.6256Z" stroke="#20234c" stroke-width="2"></path> <path d="M9 16.6256H12V18.6256H9V16.6256Z" fill="#20234c"></path> <path d="M34 16.6256H37V18.6256H34V16.6256Z" fill="#20234c"></path> <path d="M17 24.6256H29" stroke="#20234c" stroke-width="2"></path> </g></svg>
                    </template>
                    <template #heading>Dvougarážové uzavřené stání</template>
                    <template #text><a href="#">PP2&nbsp;/&nbsp;2G100</a></template>
                  </InfoComp>
                  <div class="ta-r">
                    <strong>172.480&nbsp;Kč</strong>
                  </div>
                </div>
              </div>
            </section>

            <section id=e37>
              <h3>Vlastnosti</h3>
              <div class="tags">
                <div class="tag">Útulný</div>
                <div class="tag">Zvířátka povolena</div>
                <div class="tag">Vhodný pro studenty</div>
                <div class="tag">Cash only</div>
                <div class="tag">Studená tekoucí voda</div>
                <div class="tag">Vlastní výběr rozbitého spotřebiče</div>
              </div>
            </section>

            <section id="e12">
              <h3>Speciální vybavení</h3>
              <div class="info-comp-grid sm-wrap">
                <InfoComp>
                  <template #icon><i class="fa-light fa-plug-circle-bolt"></i></template>
                  <template #heading>Elektropříprava pro předokenní žaluzie</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-air-conditioner"></i></template>
                  <template #heading>Klimatizace</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-blinds"></i></template>
                  <template #heading>Předokenní žaluzie</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-shield-check"></i></template>
                  <template #heading>Zabezpečovací zařízení</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-fan"></i></template>
                  <template #heading>Rekuperace</template>
                </InfoComp>
                <InfoComp>
                  <template #icon><i class="fa-light fa-door-closed"></i></template>
                  <template #heading>Výběr provedení podlah a dveří podle Vašich představ</template>
                </InfoComp>
              </div>
            </section>

            <section id="e24">
              <h3>Speciální vybavení</h3>
              <div class="text-columns-responsive">
                <ul class="bullet-points">
                  <li>Elektropříprava pro předokenní žaluzie</li>
                  <li>Klimatizace</li>
                  <li>Předokenní žaluzie</li>
                  <li>Zabezpečovací zařízení</li>
                  <li>Rekuperace</li>
                  <li>Výběr provedení podlah a dveří podle Vašich představ</li>
                </ul>
              </div>
            </section>

            <section id="e13">
              <h3>Speciální vybavení</h3>
              <div class="circles">
                <InfoComp class="circle">
                  <template #icon><i class="fa-duotone fa-light fa-plug-circle-bolt"></i></template>
                  <template #heading>Elektropříprava pro předokenní žaluzie</template>
                </InfoComp>
                <InfoComp class="circle">
                  <template #icon><i class="fa-duotone fa-light fa-air-conditioner"></i></template>
                  <template #heading>Klimatizace</template>
                </InfoComp>
                <InfoComp class="circle">
                  <template #icon><i class="fa-duotone fa-light fa-blinds"></i></template>
                  <template #heading>Předokenní žaluzie</template>
                </InfoComp>
                <InfoComp class="circle">
                  <template #icon><i class="fa-duotone fa-light fa-shield-check"></i></template>
                  <template #heading>Zabezpečovací zařízení</template>
                </InfoComp>
                <InfoComp class="circle">
                  <template #icon><i class="fa-duotone fa-light fa-fan"></i></template>
                  <template #heading>Rekuperace</template>
                </InfoComp>
                <InfoComp class="circle">
                  <template #icon><i class="fa-duotone fa-light fa-door-closed"></i></template>
                  <template #heading>Výběr provedení podlah a dveří podle Vašich představ</template>
                </InfoComp>
              </div>
            </section>

            <section id=e33>
              <h3>Nadstandardní položky</h3>
              <ul class="bullet-points">
                <li>Příprava rozvodů pro sušičku - zřízení samostatně jištěné zásuvky (umístěna k zásuvce pro pračku)</li>
                <li>Příplatek za elektrické přitápění v koupelnách (temperování dlažby)</li>
                <li>Výběr obkladů a dlažeb do koupelen a na WC: obklad slonová kost, dlažba slonová kost 60x120&nbsp;cm - položena na střih, série Roma</li>
                <!-- <li>Výběr zařizovacích sanitárních předmětů do koupelen a na WC: zařizovací předměty Laufen Pro, baterie série Focus E2 včetně umyvadlové bidetovéspršky na WC, ovládací tlačítko WC: AlcaPlast M571, umyvadlová sestava Cubito 60 Bílá lesk (umyvadlo + skříňka + zrcadlo se zabudovaným LEDosvětlením), umyvadlová sestava Cubito 130 Bílá lesk (umyvadlo + skříňka + zrcadlo se zabudovaným LED osvětlením)</li> -->
                <li>Výběr vypínačů a zásuvek Unica Studio Outline Aluminium</li>
                <li>Příplatek za změnu barevnosti vnitřní strany vstupních dveří NEXT: dýha dub RAL 9010 (bílá) včetně krycích lišt</li>
                <li>Příplatek za záměnu standardního kování za RX1-50 s krytím ke vstupním dveřím do jednotky</li>
                <li>Výběr bezpečnostní vložky NEXT CPS</li>
              </ul>
            </section>
            
            <section id="hypo">
              <h3>Hypoteční kalkulačka</h3>
              <div class="card">
                <!-- <p>chcete vědět jak dlouho budete platit tenhle 0+kk? CELEJ ŽIVOT! tak dlouho! nebudete mít na chleba páč budete platit 107% svý měsíční výplaty jen za tenhle bejvák. budete mít dvě práce abyste ho mohli splácet a i to bude málo.</p> -->
                <div class="range">
                  <label>Cena bytu</label>
                  <span class="range__value">8.796.113 Kč</span>
                  <!-- <span>Cena bytu: <strong>8.796.113 Kč</strong></span> -->
                </div>
                <div class="range">
                  <label for="vyse-uveru">Výše úvěru</label>
                  <!-- <span class="range__value">{{ vyseUveru }}&nbsp;Kč</span> -->
                  <!-- <input v-model="vyseUveru" type="range" id="vyse-uveru" name="vyse-uveru" min="806465" max="7258185" value="806465" style="width: 100%;"> -->
                  <span class="range__value">{{ vyseUveru }}&nbsp;Kč</span>
                </div>
                <div class="range">
                  <label for="vlastni-zdroje">Vlastní prostředky</label>
                  <span class="range__value">{{ vlastniZdroje }}&nbsp;Kč</span>
                  <input v-model="vlastniZdroje" type="range" id="vlastni-zdroje" name="vlastni-zdroje" min="806465" max="7258185" value="7258185" style="width: 100%;">
                </div>
                <div class="range">
                  <label for="splatnost">Splatnost</label>
                  <span class="range__value">{{ splatnost }}&nbsp;let</span>
                  <input v-model="splatnost" type="range" id="splatnost" name="splatnost" min="5" max="30" value="5" style="width: 100%;">
                </div>
                <div style="grid-column: -1/1;">
                  <label>Měsíční splátka</label>
                  <p><strong>15.142 Kč</strong></p>
                  <p class=stealth>Uvedené měsíční splátky platí při financování Zvýhodněnou hypotékou CENTRAL GROUP. Úroková sazba 4,79 % p.a. je platná pro fixaci úrokové sazby na 3 roky a při financování do 90 % odhadní ceny nemovitosti. Nabídka je časově omezena a platí do odvolání ze strany CENTRAL GROUP a.s.</p>
                </div>
              </div>
            </section>

            <section id="hypo3">
              <h3>Hypoteční kalkulačka</h3>
              <div class="card">
                <div class="text-columns-2">
                  <div>
                    <label for="cena-bytu2">Cena bytu</label>
                    <div :data-mask="formatCurrency(cenaBytu, jv)">
                      <input v-model="cenaBytu" type="number" name="cena-bytu2" id="cena-bytu2" placeholder="Cena bytu" readonly required>
                    </div>
                  </div>
                  <div>
                    <label for="vlastni-zdroje2">Vlastní prostředky</label>
                    <div :data-mask="formatCurrency(vlastniZdroje, jv)">
                      <input type="number" name="vlastni-zdroje2" v-model="vlastniZdroje" min="806465" max="7258185" placeholder="Vlastní prostředky" required>
                    </div>
                    <input type="range" name="vlastni-zdroje2" v-model="vlastniZdroje" min="806465" max="7258185" style="width: 100%;">
                  </div>
                  <div>
                    <label for="vyse-uveru2">Výše úvěru</label>
                    <div :data-mask="formatCurrency(vyseUveru, jv)">
                      <input v-model="vyseUveru" type="number" name="vyse-uveru2" id="vyse-uveru2" placeholder="Výše úvěru" readonly required>
                    </div>
                  </div>
                  <div>
                    <label for="splatnost2">Splatnost</label>
                    <div :data-mask="formatYear(splatnost, jv)">
                      <input type="number" placeholder="Splatnost" name="splatnost2" id="splatnost2" min="5" max="30" v-model="splatnost" required>
                    </div>
                    <input v-model="splatnost" type="range" id="splatnost2" name="splatnost2" min="5" max="30" style="width: 100%;">
                  </div>
                </div>
                <div>
                  <label style="margin-top: 0.5rem">Měsíční splátka</label>
                  <p><strong style="font-size: 1.125rem;">{{ Math.round(mesicniSplatka) }}&nbsp;Kč</strong></p>
                </div>
                <hr>
                <div>
                  <p class=stealth>Uvedené měsíční splátky platí při financování Zvýhodněnou hypotékou CENTRAL GROUP. Úroková sazba 4,79 % p.a. je platná pro fixaci úrokové sazby na 3 roky a při financování do 90 % odhadní ceny nemovitosti. Nabídka je časově omezena a platí do odvolání ze strany CENTRAL GROUP a.s.</p>
                </div>
              </div>
            </section>

          </div>
          <!-- End of left column -->

          <aside class="desktop-only" id="e14">
            <div class="card">
              <h5>Kontaktujte nás</h5>
              <!-- <div class="d-flex align-items-center">
                <i class="fa-solid fa-circle" style="font-size: 10px; color: green;">&nbsp;&nbsp;&nbsp;</i><span>Máme otevřeno</span>
              </div> -->
              <!-- <a href="#" class="btn btn-gray">+420 226 222 222</a> -->
              <!-- <a href="#" class="btn btn-gray">Kontaktní stránka</a> -->
              <a href="#" class="btn btn-gray">Sjednat schůzku</a>
              <!-- <div class="ta-c"><span>nebo</span></div> -->
              <div class="hr-line">nebo</div>
              <button class="btn btn-yellow">Rezervovat</button>
              <!-- <hr> -->
              <!-- <span class="ta-c">Další možnosti, kontakt form, adresa CG, otevírací doby, telefon, whatever</span> -->
            </div>
            <div class="card" id="e22">
              <!-- <p><strong>Kontaktujte nás</strong></p> -->
               <h5>Kontaktujte nás</h5>

                <div>
                  <form action="">
                    <label for="name">Celé jméno</label>
                    <input type="text" placeholder="Celé jméno" name="name" id=name required>
                    <label for="email">Email</label>
                    <input type="email" placeholder="Email" name="email" id="email" required>
                    <label for="phone">Telefon</label>
                    <input type="tel" name="phone" id="phone" placeholder="Telefon">
                    <label for="message">Zpráva</label>
                    <textarea name="message" id="message">Mám zájem o byt A37 v projektu Rezidenční čtvrť Tesla Hloubětín</textarea>
                    <div class="checkbox-wrapper">
                      <input type="checkbox" name="news" id="news">
                      <label for="news" name="news">Souhlasím se zasíláním novinek z nabídky CENTRAL GROUP na uvedenou e-mailovou adresu.</label>
                    </div>
                    <div class="checkbox-wrapper">
                      <input type="checkbox" name="gdpr" id="gdpr" required>
                      <label for="gdpr" name="gdpr">Souhlasím se zpracováním osobních údajů.</label>
                    </div>
                    <button class="btn btn-yellow">Rezervovat</button>
                  </form>
              </div>
              <!-- <hr> -->
              <!-- <span>Další možnosti, kontakt form, adresa CG, otevírací doby, telefon, whatever</span> -->
            </div>
            <div class="card">
              <h5>Ke stažení</h5>
              <div class="specs-table apart va-middle">
                <table>
                  <tbody>
                    <tr><td><a href="#" class="smol-link"><i class="fa-regular fa-file-pdf"></i>Karta bytu</a></td></tr>
                    <tr><td><a href="#" class="smol-link"><i class="fa-regular fa-file-pdf"></i>Technický půdorys</a></td></tr>
                    <tr><td><a href="#" class="smol-link"><i class="fa-regular fa-file-pdf"></i>Popis provedení</a></td></tr>
                  </tbody>
                </table>
              </div>
            </div>
            <div class="card" id="hypo2">
              <!-- <h5>Hypoteční kalkulačka</h5> -->
                <!-- <p>chcete vědět jak dlouho budete platit tenhle 0+kk? CELEJ ŽIVOT! tak dlouho! nebudete mít na chleba páč budete platit 107% svý měsíční výplaty jen za tenhle bejvák. budete mít dvě práce abyste ho mohli splácet a i to bude málo.</p> -->
                <div class="range">
                  <label>Cena bytu</label>
                  <span class="range__value">8.796.113 Kč</span>
                  <!-- <span>Cena bytu: <strong>8.796.113 Kč</strong></span> -->
                </div>
                <div class="range">
                  <label for="vyse-uveru">Výše úvěru</label>
                  <span class="range__value">{{ vyseUveru }}&nbsp;Kč</span>
                  <input v-model="vyseUveru" type="range" id="vyse-uveru" name="vyse-uveru" min="806465" max="7258185" value="806465" style="width: 100%;">
                  <!-- <span class="range__value">69&nbsp;420&nbsp;Kč</span> -->
                </div>
                <div class="range">
                  <label for="vlastni-zdroje">Vlastní prostředky</label>
                  <span class="range__value">{{ vlastniZdroje }}&nbsp;Kč</span>
                  <input v-model="vlastniZdroje" type="range" id="vlastni-zdroje" name="vlastni-zdroje" min="806465" max="7258185" value="7258185" style="width: 100%;">
                </div>
                <div class="range">
                  <label for="splatnost">Splatnost</label>
                  <span class="range__value">{{ splatnost }}&nbsp;let</span>
                  <input v-model="splatnost" type="range" id="splatnost" name="splatnost" min="5" max="30" style="width: 100%;">
                </div>
                <span>Měsíční splátka:</span>
                <p><strong>15.142 Kč</strong></p>
                <p class=stealth>Uvedené měsíční splátky platí při financování Zvýhodněnou hypotékou CENTRAL GROUP. Úroková sazba 4,79 % p.a. je platná pro fixaci úrokové sazby na 3 roky a při financování do 90 % odhadní ceny nemovitosti. Nabídka je časově omezena a platí do odvolání ze strany CENTRAL GROUP a.s.</p>
              </div>
            <!-- <p class="stealth ta-c">Všechny ceny jsou uváděny včetně DPH.</p> -->
          </aside>
        </div>
      </div>
    </section>

    <section id="e17">
      <div class="container">
        <h3>Galerie</h3>
        <div class="gallery">
          <img src="https://picsum.photos/200/300" alt="">
          <img src="https://picsum.photos/201/301" alt="">
          <img src="https://picsum.photos/202/302" alt="">
          <img src="https://picsum.photos/203/303" alt="">
          <img src="https://picsum.photos/204/304" alt="">
          <img src="https://picsum.photos/205/305" alt="">
          <img src="https://picsum.photos/206/306" alt="">
          <img src="https://picsum.photos/207/307" alt="">
        </div>
        <a class="expand">Rozbalit<i class="fa-regular fa-chevron-down"></i></a>
      </div>
    </section>

    <section id="e18">
      <div class="container">
        <h3>Galerie</h3>
        <Tabs>
          <Tab title="Byt">
            <h5>Fotografie</h5>
            <FancyBox class="gallery">
              <a href="https://picsum.photos/id/100/2000/1250" data-fancybox="gallery1"><img src="https://picsum.photos/id/100/200/125" alt=""></a>
              <a href="https://picsum.photos/id/101/2000/1250" data-fancybox="gallery1"><img src="https://picsum.photos/id/101/200/125" alt=""></a>
              <a href="https://picsum.photos/id/102/2000/1250" data-fancybox="gallery1"><img src="https://picsum.photos/id/102/200/125" alt=""></a>
              <a href="https://picsum.photos/id/103/2000/1250" data-fancybox="gallery1"><img src="https://picsum.photos/id/103/200/125" alt=""></a>
            </FancyBox>
            <h5>Vizualizace</h5>
            <FancyBox class="gallery">
              <a href="https://picsum.photos/id/210/2000/1250" data-fancybox="gallery2"><img src="https://picsum.photos/id/210/200/125" alt=""></a>
              <a href="https://picsum.photos/id/211/2000/1250" data-fancybox="gallery2"><img src="https://picsum.photos/id/211/200/125" alt=""></a>
              <a href="https://picsum.photos/id/212/2000/1250" data-fancybox="gallery2"><img src="https://picsum.photos/id/212/200/125" alt=""></a>
              <a href="https://picsum.photos/id/213/2000/1250" data-fancybox="gallery2"><img src="https://picsum.photos/id/213/200/125" alt=""></a>
              <a href="https://picsum.photos/id/214/2000/1250" data-fancybox="gallery2"><img src="https://picsum.photos/id/214/200/125" alt=""></a>
            </FancyBox>
          </Tab>
          <Tab title="Lokalita">
            <h5>Fotografie</h5>
            <FancyBox class="gallery">
              <a href="https://picsum.photos/id/310/2000/1250" data-fancybox="gallery3"><img src="https://picsum.photos/id/310/200/125" alt=""></a>
              <a href="https://picsum.photos/id/311/2000/1250" data-fancybox="gallery3"><img src="https://picsum.photos/id/311/200/125" alt=""></a>
              <a href="https://picsum.photos/id/312/2000/1250" data-fancybox="gallery3"><img src="https://picsum.photos/id/312/200/125" alt=""></a>
              <a href="https://picsum.photos/id/313/2000/1250" data-fancybox="gallery3"><img src="https://picsum.photos/id/313/200/125" alt=""></a>
              <a href="https://picsum.photos/id/314/2000/1250" data-fancybox="gallery3"><img src="https://picsum.photos/id/314/200/125" alt=""></a>
            </FancyBox>
            <h5>Vizualizace</h5>
            <FancyBox class="gallery">
              <a href="https://picsum.photos/id/400/2000/1250" data-fancybox="gallery4"><img src="https://picsum.photos/id/400/200/125" alt=""></a>
              <a href="https://picsum.photos/id/401/2000/1250" data-fancybox="gallery4"><img src="https://picsum.photos/id/401/200/125" alt=""></a>
              <a href="https://picsum.photos/id/402/2000/1250" data-fancybox="gallery4"><img src="https://picsum.photos/id/402/200/125" alt=""></a>
              <a href="https://picsum.photos/id/403/2000/1250" data-fancybox="gallery4"><img src="https://picsum.photos/id/403/200/125" alt=""></a>
            </FancyBox>
          </Tab>
          <Tab title="Okolí">
            <h5>Fotografie</h5>
            <FancyBox class="gallery">
              <a href="https://picsum.photos/id/510/2000/1250" data-fancybox="gallery5"><img src="https://picsum.photos/id/510/200/125" alt=""></a>
              <a href="https://picsum.photos/id/511/2000/1250" data-fancybox="gallery5"><img src="https://picsum.photos/id/511/200/125" alt=""></a>
              <a href="https://picsum.photos/id/512/2000/1250" data-fancybox="gallery5"><img src="https://picsum.photos/id/512/200/125" alt=""></a>
              <a href="https://picsum.photos/id/513/2000/1250" data-fancybox="gallery5"><img src="https://picsum.photos/id/513/200/125" alt=""></a>
              <a href="https://picsum.photos/id/514/2000/1250" data-fancybox="gallery5"><img src="https://picsum.photos/id/514/200/125" alt=""></a>
            </FancyBox>
          </Tab>
        </Tabs>
      </div>
    </section>

    <section id="e25">
      <div class="container">
        <h3>Termínové sekce</h3>
        <TimeLine>
          <TimeLinePoint class="done">
            <template #icon><i class="fa-duotone fa-light fa-calendar-day"></i></template>
            <template #heading><strong>1. termínová sekce</strong><br>17. 1. 2025</template>
            <template #text>Lorem ipsum</template>
          </TimeLinePoint>
          <TimeLinePoint class="done">
            <template #icon><i class="fa-duotone fa-light fa-calendar-day"></i></template>
            <template #heading><strong>2. termínová sekce</strong><br>15. 8. 2025</template>
            <template #text>Lorem ipsum</template>
          </TimeLinePoint>
          <TimeLinePoint>
            <template #icon><i class="fa-duotone fa-light fa-calendar-day"></i></template>
            <template #heading><strong>3. termínová sekce</strong><br>24. 10. 2025</template>
            <template #text>Lorem ipsum</template>
          </TimeLinePoint>
          <TimeLinePoint>
            <template #icon><i class="fa-duotone fa-light fa-calendar-day"></i></template>
            <template #heading><strong>4. termínová sekce</strong><br>2. 9. 2029</template>
            <template #text>Lorem ipsum</template>
          </TimeLinePoint>
        </TimeLine>
      </div>
    </section>

    <section id=e26>
      <div class="container">
        <h3>Postup výstavby</h3>
        <ol class="progress">
          <li class="progress__done">
            <InfoComp class="circle">
              <template #icon><i class="fa-duotone fa-light fa-excavator"></i></template>
              <template #heading>Zahájení výstavby</template>
              <template #text>Květen 2024</template>
            </InfoComp>
          </li>
          <li class="progress__arrow">
            <i class="fa-light fa-arrow-right"></i>
          </li>
          <li class="progress__done">
            <InfoComp class="circle">
              <template #icon><i class="fa-duotone fa-light fa-wallet"></i></template>
              <template #heading>Zahájení prodeje</template>
              <template #text>Říjen 2024</template>
            </InfoComp>
          </li>
          <li class="progress__arrow">
            <i class="fa-light fa-arrow-right"></i>
          </li>
          <li class="progress__current">
            <InfoComp class="circle">
              <template #icon><i class="fa-duotone fa-light fa-trowel-bricks"></i></template>
              <template #heading>Dokončení hrubé stavby</template>
              <template #text>Říjen 2025</template>
            </InfoComp>
          </li>
          <li class="progress__arrow">
            <i class="fa-light fa-arrow-right"></i>
          </li>
          <li>
            <InfoComp class="circle">
              <template #icon><i class="fa-duotone fa-light fa-truck-moving"></i></template>
              <template #heading>Předpokládaný termín nastěhování</template>
              <template #text>Prosinec 2026</template>
            </InfoComp>
          </li>
        </ol>
      </div>
    </section>

    <section id=e27>
      <div class="container">
        <h3>Seznam nadstandardních položek</h3>
        <ul class="bullet-points">
          <li>Příprava rozvodů pro sušičku - zřízení samostatně jištěné zásuvky (umístěna k zásuvce pro pračku)</li>
          <li>Příplatek za elektrické přitápění v koupelnách (temperování dlažby)</li>
          <li>Výběr obkladů a dlažeb do koupelen a na WC: obklad slonová kost, dlažba slonová kost 60x120&nbsp;cm - položena na střih, série Roma</li>
          <li>Výběr zařizovacích sanitárních předmětů do koupelen a na WC: zařizovací předměty Laufen Pro, baterie série Focus E2 včetně umyvadlové bidetové spršky na WC, ovládací tlačítko WC: AlcaPlast M571, umyvadlová sestava Cubito 60 Bílá lesk (umyvadlo + skříňka + zrcadlo se zabudovaným LED osvětlením), umyvadlová sestava Cubito 130 Bílá lesk (umyvadlo + skříňka + zrcadlo se zabudovaným LED osvětlením)</li>
          <li>Výběr vypínačů a zásuvek Unica Studio Outline Aluminium</li>
          <li>Příplatek za změnu barevnosti vnitřní strany vstupních dveří NEXT: dýha dub RAL 9010 (bílá) včetně krycích lišt</li>
          <li>Příplatek za záměnu standardního kování za RX1-50 s krytím ke vstupním dveřím do jednotky</li>
          <li>Výběr bezpečnostní vložky NEXT CPS</li>
        </ul>
      </div>
    </section>

    <section id="e34">
      <div class="container">
        <h3>Mapa lokality</h3>
        <div class="tags">
          <button class="tag">Doprava</button>
          <button class="tag">Zábava</button>
          <button class="tag">Rekreace</button>
          <button class="tag">Jídlo</button>
        </div>
        <div class="card p-0">
          <img src="https://www.central-group.cz/Uloziste/fa/facc97ed-b264-4141-b652-289c41441212.jpg" alt="" style="width: 100%; height: 550px; object-fit: cover; max-height: 60vh;">
        </div>
      </div>
    </section>

    <section class="mobile-only" id="e7">
      <div class="container">
        <h3>Ke stažení</h3>
        <div class="card">
          <div class="specs-table apart va-middle">
            <table>
              <tbody>
                <tr><td><a href="#" class="smol-link"><i class="fa-regular fa-file-pdf"></i>Karta bytu</a></td></tr>
                <tr><td><a href="#" class="smol-link"><i class="fa-regular fa-file-pdf"></i>Technický půdorys</a></td></tr>
                <tr><td><a href="#" class="smol-link"><i class="fa-regular fa-file-pdf"></i>Popis provedení</a></td></tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </section>

    <section id="e35">
      <div class="container">
        <h3>Podobné byty</h3>
        <div class="card-apt--list">
          <AptCard></AptCard>
          <AptCard></AptCard>
          <AptCard></AptCard>
          <AptCard></AptCard>
        </div>
      </div>
    </section>

    <section id="e36">
      <div class="container">
        <h3>Podobné byty</h3>
        <SuggestedApts>
          <AptCard></AptCard>
          <AptCard></AptCard>
          <AptCard></AptCard>
          <AptCard></AptCard>
          <AptCard></AptCard>
          <AptCard></AptCard>
        </SuggestedApts>
      </div>
    </section>

    <section>
      <div class="container">
        <p class="stealth">Uvedená vyobrazení (zejména půdorysu a návrhu zařízení interiérů) jsou pouze ilustrativní a nemusí zcela odpovídat stavebně-technickému řešení jednotky. Vyobrazený nábytek, kuchyňská linka, spotřebiče a další prvky vybavení domácnosti jsou pouze příkladné a nejsou plněním CENTRAL GROUP, není-li výslovně sjednáno jinak. Přesný rozsah plnění je specifikován ve smlouvě.</p>
        <!-- <p class="stealth">Všechny ceny jsou uváděny včetně DPH.</p> -->
      </div>
    </section>

    <aside class="mobile-only">
      <div class="card thin">
        <!-- <button id="mobile-sticky-expand" onclick="$(this).next().slideToggle('fast'); $(this).find('i').toggleClass('fa-chevron-up fa-chevron-down')"><i class="fa-light fa-chevron-up"></i></button>
        <div style="display: none;">
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur ab quia rem modi culpa consequatur nisi aliquam, vitae omnis quod odit mollitia doloribus, pariatur iusto quibusdam aperiam, labore dolorem sed.</p>
          <a href="#" class="btn btn-gray">Sjednat schůzku</a>
        </div> -->
        <a href="#" class="btn btn-yellow">Rezervovat</a>
      </div>
    </aside>

    <div class="hidden">
      <!-- SQUIRCLES -->
      <svg class="hidden" viewBox="0 0 1 1" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <clipPath id="SquircleClip-1" clipPathUnits="objectBoundingBox">
            <path d="M 0,0.5
                      C 0,0  0,0  0.5,0
                        1,0  1,0  1,0.5
                        1,1  1,1  0.5,1
                        0,1  0,1  0,0.5"></path>
          </clipPath>
          <clipPath id="SquircleClip-2" clipPathUnits="objectBoundingBox">
            <path d="M 0,0.5
                      C 0,0.0575  0.0575,0  0.5,0
                        0.9425,0  1,0.0575  1,0.5
                        1,0.9425  0.9425,1  0.5,1
                        0.0575,1  0,0.9425  0,0.5"></path>
          </clipPath>
          <clipPath id="SquircleClip-3" clipPathUnits="objectBoundingBox">
            <path d="M 0,0.5
                      C 0,0.115  0.115,0  0.5,0
                        0.885,0  1,0.115  1,0.5
                        1,0.885  0.885,1  0.5,1
                        0.115,1  0,0.885  0,0.5"></path>
          </clipPath>
          <clipPath id="SquircleClip-4" clipPathUnits="objectBoundingBox">
            <path d="M 0,0.5
                      C 0,0.1725  0.1725,0  0.5,0
                        0.8275,0  1,0.1725  1,0.5
                        1,0.8275  0.8275,1  0.5,1
                        0.1725,1  0,0.8275  0,0.5"></path>
          </clipPath>
          <clipPath id="SquircleClip-5" clipPathUnits="objectBoundingBox">
            <path d="M 0,0.5
                      C 0,0.23  0.23,0  0.5,0
                        0.77,0  1,0.23  1,0.5
                        1,0.77  0.77,1  0.5,1
                        0.23,1  0,0.77  0,0.5"></path>
          </clipPath>
        </defs>
      </svg>
    </div>

  </main>
</template>

<!-- MARK: STYLE -->
<style scoped>

  main{
    background-color: var(--color-superwhite, #fcfcfc);
  }

  section{
    position: relative;
  }

  section{
    margin-block: 2rem;
  }
  
  section:first-child{
    margin-top: 0;
  }
  section:last-child{
    margin-bottom: 0;
  }

  img{
    /* object-fit: cover; */
  }

  h2 a {
      text-decoration: none;

      &:hover,
      &:active {
        text-decoration: underline;
      }
  }

  .heading{
    display: flex;
    align-items: center;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  h1{
    font-size: 2rem;
    font-weight: 700;
    line-height: 1;
  }

  h2{
    font-size: 22px;
    /* font-size: 20px; */
    margin: 0;
    font-weight: 600;
    /* display: flex; */
    /* flex-direction: column; */
    line-height: 1.3333;
  }

  h2 > *+*::before{
    content: '|';
    /* content: '•'; */
    margin: 0 0.25em;
    opacity: 0.333;
    font-weight: 200;
    
  }

  h2.comma{
    flex-direction: row;

    & > *+*::before{
      margin: 0;
      content: ', ';
      opacity: 1;

      /* display: none; */
    }
  }

  h2 [class*="fa"]{
    font-size: 0.85em;
    width: 1.0rem;
    margin-right: 0.5rem;
    text-align: center;
  }

  h3{
    font-size: 22px;
  }


  h5{
    font-size: 1rem;
    margin-top: 1.5rem;
    margin-bottom: 1rem;
    font-weight: 600;
    /* maybe? */
    color: var(--color-blue, #20234c);
  }

  h3+h5{
    margin-top: 1rem;
  }

  .main-map{
    margin-block: -0.5rem;
  }

  #e23,
  #e39{
    margin-block: -0.5rem;

    .card {
      padding: 0;
    }
  }
  
  .trinity{
    display: flex;
    gap: 0.5rem 1.25rem;
    flex-wrap: wrap;
    /* font-size: 14px; */
    font-weight: 500;
    line-height: 1.5;
    flex-direction: row;
    margin: 1rem 0;

    & > *{
      display: flex;
      align-items: center;
    }

    [class*="fa"]{
      --trinity-icon-size: 18px;
      font-size: var(--trinity-icon-size);
      width:     var(--trinity-icon-size);
      margin-right: 10px;
      text-align: center;
      /* vertical-align: middle; */
      /* maybe? */
      color: var(--color-blue, #20234c);
    }
  }

  .price{
    font-size: 1.5rem;
    margin: 1.25rem 0 0.5rem;
    line-height: 1;
    color: black;
  }


  @media screen and (max-width: 991px){
    h1{
      font-size: 1.625rem;
    }

    h2{
      font-size: 20px;
      display: flex;
      flex-direction: column;
      line-height: 1.15;
    }

    h2 > *+*::before{
      content: none;
      display: none;
    }
  }

  .small {
    font-size: 0.875rem;
  }


  .main-layout{
    display: grid;
    gap: 0rem 1.5rem;
    grid-template-columns: 1fr;
    position: relative;
  }


  @media screen and (min-width: 992px) {
    .main-layout{
      grid-template-columns: 62% 1fr;
      grid-template-rows: auto 1fr;
      align-items: start;
    }
  }



  .prim-rack--wrapper{
    /* hacky as shit but it's not like it matters */
    max-width: calc(100vw - 72px);
  }

  .prim-rack {
    display: flex;
    flex-direction: column;
    /* align-items: center; */
  } 

  .prim-rack img{
    cursor: pointer;
    /* temp hidden */
    width: 0px;
  }

  .prim-rack > .card{
    width: 100%;
    padding: 0;
    border-radius: 14px;
    /* clip-path: url(#SquircleClip-2); */

    img{
      /* aspect-ratio: 1; */
      width: 100%;
      height: 100%;
      /* object-fit: contain; */
      object-fit: cover;
    }
  }

  .prim-rack--aside{
    display: flex;
    flex-direction: column;
    gap: 1rem;

    /* TEMP: vyp */
    display: none;

    img{
      object-fit: contain;
      max-height: 178px;
      cursor: pointer;
    }
  }

  .specs-table {
    margin-block: -0.5rem;
    /* todo: consider font-size */
    font-size: 0.875rem;
  }

  .prim-in{
    display: grid;
    gap: 1.0rem 1.5rem;
    grid-template-columns: 62% 1fr;
  }

  @media screen and (max-width: 767px) {
    .prim-in{
      grid-template-columns: 1fr;
    }
  }


  .headings {
    line-height: 1;;
  }

  .overview{
    display: flex;
    gap: 10px;

    & > * {
      flex: 1 1 auto;
    }
  }

  .overview .actions {
    display: flex;
    flex-direction: column;
    gap: 4px;
    margin-top: -4px;
    justify-content: start;
    flex: 0 0 auto;
  }

  .action{
    align-items: center;
    appearance: none;
    aspect-ratio: 1;
    background-color: white;
    border-radius: 999px;
    border: 1px solid #f1f1f1;
    color: inherit;
    cursor: pointer;
    display: inline-flex;
    font-size: 16px;
    height: 40px;
    justify-content: center;
    outline: none;
    text-align: center;
    transition: background-color 0.1s;
    width:  40px;
  }

  .prim-img--container{
    /* height: 550px; */
    width: 100%;
    aspect-ratio: 1;
    padding: 2rem;
    display: flex;
    align-items: center;
    /* temp */
    /* background: radial-gradient(transparent 50%, #00000007); */
    max-height: 500px;

    /* max-height: 274px; */
    /* padding: 8px; */
  }

  .prim-img{
    max-height: 100%;
    max-width: 100%;
    /* aspect-ratio: 1; */
    object-fit: contain;
    margin: auto;
  }

  .status{
    display: flex;
    justify-content: center;
    font-size: 0.75rem;
  }

  .buttons-holder{
    display: flex;
    gap: 0.5rem;
  }


  .info-comps {
    /* Grid */
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: 1fr;
    width: 100%;
    margin: 0;
    padding-inline: min(6px, 5%);
    margin-top: -0.5rem;
    max-width: 580px;
    gap: 0.5rem 0rem;

    display: flex;
    flex-direction: row;
    /* flex-wrap: wrap; */

    & > *{
      flex: 1 1 0;
    }
  }

  .info-comps.separators{
      .info-comp{
        justify-content: center;
        padding: 0 0.5rem;
      }
  }

  @media screen and (min-width: 575px) {
    .info-comps.separators .info-comp+.info-comp {
      border-left: 1px solid var(--color-gray-mid);
    }
  }

  

  /* # GALLERY */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(min(100%, 176px), 1fr));
    gap: 6px;
    position: relative;
    overflow: clip;

    &::after{
      /* content: ''; */
      display: block;
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      height: 35px;
      user-select: none;
      background: linear-gradient(transparent, white);
    }

    & img{
      display: block;
      width: 100%;
      height: 100%;
      aspect-ratio: 1.6;
      object-fit: cover;
      background-color: white;
      border: 1px solid #f1f1f1;
      border-radius: 6px;
      position: relative;
      overflow: clip;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
      /* clip-path: url(#SquircleClip-2); */
    }
  }




  .expand {
    display: flex;
    align-items: center;
    font-family: inherit;
    appearance: none;
    justify-content: center;
    width: fit-content;
    margin: 1rem auto;
    gap: 0.5em;
    line-height: 1;
    border-radius: 999px;
    padding: 0.6em 1.25em;
    user-select: none;
    cursor: pointer;
    -webkit-tap-highlight-color: transparent;
    transition: background-color 0.1s;

    &:hover {
      /* background-color: var(--color-gray-light); */
    }

    [class*="fa"]{
      font-size: 70%;
      margin-bottom: -3%;
    }
  }
  
  .stealth{
    font-size: 0.75rem;
    color: var(--color-gray-dark);    
    opacity: 50%;
  }


  .map img{
    border: 1px solid var(--color-gray-light);
    border-radius: 5px;
    margin-bottom: 0.75rem;
    cursor: pointer;
  }

  .map a{
    color: inherit;
    text-decoration: none;
  }


  hr {
    height: 1px;
    /* background-color: rgba(0, 0, 0, 0.15); */
    background-color: var(--color-gray-mid, #e4e4e4);
    margin: 1rem auto;

    &.tighten{
      margin: -0.5rem 0;
    }
  }

  aside{
    line-height: 1.25;


  }

  aside h5{
    text-align: center;
    font-weight: 600;
    margin: 0.5rem 0 0.25rem;
    color: var(--color-blue, #20234c);
  }

  aside .card h5{
    text-align: center;
    margin: 0 0 1rem;
  }

  aside.desktop-only{
    position: sticky;
    top: 16px;
    /* Sticky header */
    top: calc(var(--header-height) + 16px);
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  aside .btn {
    margin-block: 0.75rem;

    &:first-child{margin-top: 0;}
    &:last-child{margin-bottom: 0;}
  }

  aside.mobile-only{
    position: fixed;
    bottom: 0;
    width: 100%;
    z-index: 10;
  }

  .dotted-underline{
    text-decoration: underline dotted 1px #949494;
    text-underline-offset: 0.25rem;
  }

  .info-comp-grid{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.25rem 1rem;
    /* padding: 0.5rem 0; */
  }

  @media screen and (max-width: 575px){
    .info-comp-grid.sm-wrap{
      grid-template-columns: 1fr;
    }
    
  }

  .info-comp-grid.specs{
    gap: 1rem 3rem;
    grid-template-columns: auto auto 1fr;
    align-items: baseline;
  }

  .info-comp-grid.specs-2{
    gap: 1rem 3rem;
    grid-template-columns: auto 1fr;
    align-items: baseline;
  }

  @media screen and (max-width: 991px) {
    .info-comp-grid.specs{
      gap: 0.75rem 1.5rem;
      grid-template-columns: 1fr 1fr 1fr;
    }

    .info-comp-grid.specs-2{
      /* gap: 0.75rem 1.5rem; */
      grid-template-columns: 1fr 1fr 1fr;
    }
  }

  @media screen and (max-width: 767px) {
    .info-comp-grid.specs-2{
      grid-template-columns: auto 1fr;
    }
  }

  @media screen and (max-width: 575px){
    .info-comp-grid.specs{
      grid-template-columns: 1fr 1fr;
    }
    .info-comp-grid.specs-2{
      grid-template-columns: 1fr;

      /* TEMP */
      column-gap: 0;
      grid-template-columns: 1fr 1fr;
    }
  }

  /* width 299px */
  @media screen and (max-width: 299px){
    .info-comp-grid.specs{
      grid-template-columns: 1fr;
    }
  }

  .smol-link{
    text-decoration: none;
    display: flex;
    width: fit-content;
    align-self: center;
    /* gap: 8px; */
    margin: 0.25rem 0;
    line-height: 1;

    &:hover{
      text-decoration: underline;
    }

    [class*="fa"]{
      font-size: 18px;
      /* width: 18px; */
      margin-right: 0.5rem;
    }
  }

  @media screen and (max-width: 991px){
    .desktop-only{
      display: none !important;
    }
  }

  @media screen and (min-width: 992px){
    .mobile-only{
      display: none !important;
    }
  }

  .card .specs-table table{
    margin: 0;
    /* background-color: red; */
  }

  .cards{
    margin: -5px;

    .card {
      margin: 5px;
    }
  }


  
  .cards-rows{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 5px;
    font-size: 14px;
  }

  @media screen and (max-width: 575px){
    .cards-rows{
      grid-template-columns: 1fr;
    }
    
  }

  .cards-squared{
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    gap: 0.5rem;
    /* align-items: start; */
    
    .card{
      flex-direction: column;
      align-items: center;
      text-align: center;
      min-width: 150px;
    }
  }

  .amenity{
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-direction: row;
    gap: 6px;
    height: 100%;
  }

  a.amenity, .amenity a{
    text-decoration: none;
    color: var(--color-blue, #20234c);

    &:hover{
      text-decoration: underline;
    }
  }

  .circles {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(min(100%, 150px), 1fr));
    align-items: baseline;
    gap: 1.5rem 0.25rem;
  }

  .separator-underline{
    display: block;
    width: 100%;
    padding-bottom: 0.5rem;
    margin-bottom: 0.75rem;
    border-bottom: 1px solid var(--color-gray-mid, #e4e4e4);

    .card & {
      border-bottom: 1px solid rgba(0, 0, 0, 0.15);
    }
  }

  #mobile-sticky-expand{
    appearance: none;
    border: none;
    outline: none;
    margin: 0 auto 0.75rem;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: transparent;
    color: var(--color-gray-dark);
    opacity: 0.5;
    font-size: 100%;
  }

  .card-apt--list{
    display: flex;
    overflow: auto;
    width: 100%;
    gap: 12px;
    padding: 0px 0px 5px;
    scrollbar-width: thin;
    /* opts element (scroll container) into scroll snapping */
    scroll-snap-type: x mandatory;

    .card-apt{
      width: 100%;
      max-width: 330px;
      flex: 1 0 auto;
      /* Disabled scroll overshoot (maintained momentum) */
      scroll-snap-stop: always;
      /* Alignment */
      scroll-snap-align: center;
    }
  }

  .range{
    display: grid;
    grid-template-columns: 1fr 1fr;
    /* grid-template-rows: 1fr 1fr; */
    font-size: 0.875rem;
    margin-bottom: 0.75rem;
    accent-color: var(--color-blue, #20234c);

    
    input[type="range"]{
      grid-column: 1/-1;
      width: 100%;
    }

    .range__value{
      text-align: right;
      font-weight: 700;
    }
  }

  .text-columns-2{
    column-count: 2;
  }

  .text-columns-responsive{
    column-width: 265px;
  }

  /* .text-columns-responsive{
    column-count: 1;
  }

  @media screen and (min-width: 576px) {
    .text-columns-responsive{
      column-count: 2;
    }
  }

  @media screen and (min-width: 768px) {
    .text-columns-responsive{
      column-count: 3;
    }
  }

  @media screen and (min-width: 992px) {
    .text-columns-responsive{
      column-count: 2;
    }
  } */

  .progress{
    display: flex;
    list-style: none;
    align-items: baseline;
    gap: 0.5rem 0rem;
    width: 100%;
    overflow: auto;
    scrollbar-width: thin;

    li {
      display: flex;
      flex: 1 0 160px;
      max-width: 220px;
    }

    .progress__arrow {
      font-size: 1.5rem;
      flex: 0;
    }
  }

  .pohledy {
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: 1fr;
    width: 100%;
    align-items: stretch;
    gap: 0px 5px;

    figure {
      display: flex;
      flex-direction: column;
    }

    figcaption {
      line-height: 1;
      font-size: 0.875rem;
      align-self: center;
      /* text-align: center; */
      margin-bottom: 0.5rem;

      /* display: none; */
    }

    img{
      object-fit: contain;
      object-position: center;
      mix-blend-mode: multiply;
      height: 100%;
      max-height: 150px;
      margin: 0 auto;
    }
  }

  @supports (grid-template-rows: subgrid) {
    .pohledy {
      figure {
        display: grid;
        grid-template-rows: subgrid;
        grid-row: span 2;
      }
    }
  }

.tags{
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 5px;
  margin-block: 1rem;    
}

.tag{
  /* -webkit-user-select: none; */
  appearance: none;
  align-items: center;
  background-color: white;
  border-radius: 6px;
  border: 1px solid #e6e6e6;
  display: inline-flex;
  font-size: 0.875rem;
  font-weight: 500;
  color: inherit;
  gap: 0.5em;
  letter-spacing: -0.015em;
  line-height: 1;
  min-height: 2rem;
  padding: 0 0.8rem;
  position: relative;
  /* user-select: none; */
  vertical-align: middle;
}

.tag__del{
  cursor: pointer;
  font-size: 80%;
  vertical-align: middle;
  position: relative;
  -webkit-tap-highlight-color: transparent;
  padding: 5px;
  margin: -5px;
  border-radius: 999px;
  /** creates new stacking context **/
  isolation: isolate;
}

.tag__del::before {
  content: '';
  display: block;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 1.75em;
  height: 1.75em;
  aspect-ratio: 1;
  background: rgba(0, 0, 0, 0.05);
  z-index: -1;
  border-radius: 999px;
  transition: opacity 100ms;
  opacity: 0;
}

.rooms-counter {
  counter-reset: rooms-counter; 
}

.rooms-counter li {
  counter-increment: rooms-counter;
}

.rooms-counter li::marker {
  content: counter(rooms-counter, decimal) '.';
}



  /* ====== !!!!! ====== */
  #e2,
  #e4,
  #e5,
  #e8,
  #e9,
  #e10,
  #e13,
  #e17,
  #e20,
  #e22,
  #e11,
  #e21,
  #e24,
  #e28,
  #hypo, #hypo2,
  #e30,
  #e31, #e31+hr,
  #e32,
  #e27,
  #e25,
  #e35,
  #e37,
  /* #e39, */
  #e23,
  #e1
  {
    display: none;
  }

</style>