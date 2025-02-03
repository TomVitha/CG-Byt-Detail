<script setup>
  import PInfo from '../components/PInfo.vue'

  import Tabs from '../components/tabs/CTabs.vue'
  import Tab from '../components/tabs/CTab.vue'

  import SpecsTable1 from '../components/SpecsTable1.vue'
  import SpecsTable2 from '../components/SpecsTable2.vue'
</script>

<template>
  <!-- Here's where the magic happens -->
  <main>
    <section>
      <div class="container">
        <div class="headings">
          <div class="heading">
            <h1>Byt&nbsp;D64</h1>
            <span class="status status--available">Volný</span>
          </div>
          <div class="subh">
            <h2>Rezidence Basilejské náměstí</h2>
          </div>
          <h3>Praha&nbsp;3 &#8209; Žižkov</h3>
        </div>
      </div>
    </section>
    <section>
      <div class="container">
        <div class="prim">
          <div class="p-infos">
            <PInfo>
              <template #icon><i class="fa-light fa-border-all"></i></template>
              <template #heading>Dispozice</template>
              <template #text>5+kk</template>
            </PInfo>
            <PInfo>
              <template #icon><i class="fal fa-building"></i></template>
              <template #heading>Podlaží</template>
              <template #text>8.&nbsp;patro</template>
            </PInfo>
            <PInfo>
              <template #icon><i class="fa-light fa-ruler-combined"></i></template>
              <template #heading>Plocha</template>
              <template #text>174&nbsp;m²</template>
            </PInfo>
          </div>
          <div class="prim-in cardd">
            <div class="prim-img--container">
              <img class="prim-img" src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" alt="">
            </div>
            <div class="prim-rack--wrapper">
              <div class="prim-rack">
                <div class="cardd"><img class="prim-img" src="https://www.central-group.cz/Uloziste/98/98318170-6515-40df-b1f7-69e9156608b3.gif" alt="Půdorys bytu"></div>
                <div class="cardd"><img class="prim-img" src="https://www.central-group.cz/Uloziste/68/68703066-8b96-4925-abcd-77670b0f7b75.png" alt="Půdorys podlaží"></div>
                <div class="cardd"><img class="prim-img" src="https://www.central-group.cz/Uloziste/fd/fdbd0cb2-9fa8-4a19-95be-97e509ea2ad7.gif" alt="Pohled na dům s vyznačením patra"></div>
                <div class="cardd"><img class="prim-img" src="https://www.central-group.cz/Uloziste/8f/8fff6b6e-772c-4278-9f6f-47b7f798135f.png" alt="Situační plánek lokality"></div>
              </div>
            </div>
            <div class="actions">
              <div class="action fav"><i class="fal fa-heart"></i></div>
              <!-- <div class="action"><i class="fa-light fa-calculator"></i></div> -->
            </div>
          </div>
          <div class="prim-data">
            
            <Tabs class="bullet">
              <Tab title="Základní info">
                <SpecsTable1 />
              </Tab>
              <Tab title="Místnosti">
                <SpecsTable2 />
              </Tab>
            </Tabs>
            <div class="buttons-holder">
              <a href="#" class="btn btn-yellow">Rezervovat</a>
            </div>
            <p class="stealth">Všechny ceny jsou uváděny včetně DPH.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- <section>
      <div class="container">
        <div class="plan">
          <figure>
            <figcaption>Situační plánek lokality</figcaption>
            <img src="https://www.central-group.cz/Uloziste/68/68703066-8b96-4925-abcd-77670b0f7b75.png" alt="Půdorys podlaží">
          </figure>
          <figure>
            <figcaption>Pohled na dům s vyznačením patra</figcaption>
            <img src="https://www.central-group.cz/Uloziste/fd/fdbd0cb2-9fa8-4a19-95be-97e509ea2ad7.gif" alt="Pohled na dům s vyznačením patra">
          </figure>
          <figure>
            <figcaption>Půdorys podlaží</figcaption>
            <img src="https://www.central-group.cz/Uloziste/8f/8fff6b6e-772c-4278-9f6f-47b7f798135f.png" alt="Situační plánek lokality">
          </figure>
        </div>
      </div>
    </section> -->

    <section>
      <div class="container">
        <h3>Ke stažení</h3>
        <div class="buttons-holder">
          <a href="#" class="btn btn-gray inline">Karta bytu<i class="fa-regular fa-file-pdf"></i></a>
          <a href="#" class="btn btn-gray inline">Technický půdorys<i class="fa-regular fa-file-pdf"></i></a>
          <a href="#" class="btn btn-gray inline">Detail bytu<i class="fa-regular fa-file-pdf"></i></a>
        </div>
      </div>
    </section>

    <section>
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

    <section>
      <div class="container">
        <h3>Seznam nadstandardních položek</h3>
        <ul class="bullet-points">
          <li>Příprava rozvodů pro sušičku - zřízení samostatně jištěné zásuvky (umístěna k zásuvce pro pračku)</li>
          <li>Příplatek za elektrické přitápění v koupelnách (temperování dlažby)</li>
          <li>Výběr obkladů a dlažeb do koupelen a na WC: obklad slonová kost, dlažba slonová kost 60x120&nbsp;cm - položena na střih, série Roma</li>
          <li>
            Výběr zařizovacích sanitárních předmětů do koupelen a na WC: zařizovací předměty Laufen Pro, baterie série Focus E2 včetně umyvadlové bidetové
            spršky na WC, ovládací tlačítko WC: AlcaPlast M571, umyvadlová sestava Cubito 60 Bílá lesk (umyvadlo + skříňka + zrcadlo se zabudovaným LED
            osvětlením), umyvadlová sestava Cubito 130 Bílá lesk (umyvadlo + skříňka + zrcadlo se zabudovaným LED osvětlením)
          </li>
          <li>Výběr vypínačů a zásuvek Unica Studio Outline Aluminium</li>
          <li>Příplatek za změnu barevnosti vnitřní strany vstupních dveří NEXT: dýha dub RAL 9010 (bílá) včetně krycích lišt</li>
          <li>Příplatek za záměnu standardního kování za RX1-50 s krytím ke vstupním dveřím do jednotky</li>
          <li>Výběr bezpečnostní vložky NEXT CPS</li>
        </ul>
      </div>
    </section>

    <section>
      <div class="container">
        <h3>Mapa lokality</h3>
        <img src="https://www.central-group.cz/Uloziste/fa/facc97ed-b264-4141-b652-289c41441212.jpg" alt="">
      </div>
    </section>

    <section>
      <div class="container">
        <p class="stealth">
          Uvedená vyobrazení (zejména půdorysu a návrhu zařízení interiérů) jsou pouze ilustrativní a nemusí zcela odpovídat stavebně-technickému řešení jednotky. Vyobrazený nábytek, kuchyňská linka, spotřebiče a další prvky vybavení domácnosti jsou pouze příkladné a nejsou plněním CENTRAL GROUP, není-li výslovně sjednáno jinak. Přesný rozsah plnění je specifikován ve smlouvě.
        </p>
      </div>
    </section>

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

<style scoped>

  main{
    background-color: var(--color-superwhite, #fcfcfc);
  }

  section{margin-block: 1.5rem;}
  section:first-child{margin-top: 14px;}
  /* section:last-child{margin-bottom: 0;} */

  img{
    object-fit: cover;
  }

  h1{
    font-size: 2.25rem;
    font-weight: 700;
    margin: 0.15em 0 0.1em;
  }

  .heading{
    display: flex;
    align-items: center;
    gap: 1rem;
    line-height: 1;
  }


  .headings h2 {
    margin: 0;
    margin-top: 0.3em;
    font-size: 1.375rem;
    font-weight: 400;
    line-height: 1.15;
  }

  .headings h3{
    margin: 0;
    font-weight: 400;
    font-size: 1rem;
  }

  h2 {
    margin: 1.5rem 0;
  }

  @media screen and (max-width: 575px){
    h1{
      font-size: 2rem;
    }
    .headings h2 {
      font-size: 18px;
    }
    
  }

  /* # Mobile-first grid */

  /* I have no fucking clue what to call this so it's .prim temporarily... temporarily, right?? */
  .prim{
    display: grid;
    gap: 1.25rem 2rem;
    grid-template-columns: 1fr;
  }

  /* Container for gallery */
  .prim-in{
    position: relative;
  }


  @media screen and (min-width: 992px) {
    .prim{
      /* grid-template-columns: 1.618fr 1fr; */
      grid-template-columns: 63% 1fr;
      grid-template-rows: auto 1fr;
      align-items: start;
    }

    .prim-in{
      grid-row: span 2;
      order: -1;
    }
  }

  .prim-in img{
    cursor: pointer;
  }

  .prim-rack--wrapper{
    /* hacky as shit but it's not like it matters */
    max-width: calc(100vw - 72px);
  }

  .prim-rack {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 0.5rem;
    overflow: auto;
    
  }

  .prim-rack > .cardd{
    width:  90px;
    height: 90px;
    aspect-ratio: 1;
    /* padding: 10px; */
    padding: 0;
    border-radius: 10px;
    /* clip-path: url(#SquircleClip-2); */

    img{
      /* aspect-ratio: 1; */
      width: 100%;
      height: 100%;
      /* object-fit: contain; */
      object-fit: cover;
    }
  }

  .specs-table {
    font-size: 0.875rem;
  }

  .actions{
    position: absolute;

    display: flex;
    flex-direction: column;
    gap: 0.25rem;
    /* visibility: hidden; */
    right:  0px;
    top:    0px;
    padding: inherit;
  }

  .prim-in:hover .actions{
    visibility: visible;
  }

  .action{
    width:  2.5rem;
    height: 2.5rem;
    aspect-ratio: 1;
    /* background-color: rgba(0,0,0,0.5); */
    border-radius: 999px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    cursor: pointer;
    /* color: white; */
    transition: background-color 0.1s;
  }
  /* .action:hover{background-color: rgba(0,0,0,0.6);} */
  /* .action:active{background-color: rgba(0,0,0,0.7);} */

  .prim-img--container{
    /* height: 550px; */
    width: 100%;
    aspect-ratio: 1;
    padding: 2rem;
    display: flex;
    align-items: center;
    /* temp */
    /* background: radial-gradient(transparent 50%, #00000007); */
    max-height: 600px;
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

  .p-infos {
    display: flex;
    /* align-items: baseline; */
    justify-content: center;
    gap: 1rem 5%;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }

  @media screen and (min-width: 992px) {
    .p-infos{
      margin-block: 0.5rem;
    }
  }

  /* # GALLERY */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(min(100%, 120px), 1fr));
    gap: 0.5rem;
    position: relative;
    /* max-height: 200px; */
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

    &>img{
      display: block;
      width: 100%;
      height: 100%;
      aspect-ratio: 1;
      object-fit: cover;
      cursor: pointer;

      background-color: white;
      border: 1px solid #f1f1f1;
      /* border-radius: 24px; */
      /* clip-path: url(#SquircleClip-2); */
      border-radius: 10px;
      position: relative;
      overflow: clip;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
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
    margin: 0.75rem 0;
    opacity: 50%;
  }

  .plan{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 1rem;

    .card {
      padding: 0;
    }

    figure{
      display: flex;
      flex-direction: column;
    }

    figcaption {
      margin-bottom: 0.5rem;
    }

    img{
      width: 100%;
      height: 100%;
      /* aspect-ratio: 1; */
      flex: 1;
      object-fit: contain;
      cursor: pointer;
      background-color: white;
      border-radius: 10px;
      border: 1px solid #f1f1f1;
    }
  }

  @media screen and (max-width: 767px){
    .plan{
      grid-template-columns: 1fr 1fr;
    }
  }

  @media screen and (max-width: 575px){
    .plan{
      grid-template-columns: 1fr;
    }
    
  }

</style>