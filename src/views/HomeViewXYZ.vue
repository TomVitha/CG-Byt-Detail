<script setup>
  import PInfo from '../components/PInfo.vue'

  import SpecsTable1 from '../components/SpecsTable1.vue'
  import SpecsTable2 from '../components/SpecsTable2.vue'

  import Breadcrumbs from '../components/BreadCrumbs.vue'
  import BreadcrumbsMy from '../components/BreadCrumbsMy.vue'
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
      <div class="container">
        <div class="prim-in grid-golden-ratio cardd">
          <div class="prim-img--container">
            <img class="prim-img" src="https://www.central-group.cz/Uloziste/f8/f8312d63-b478-44ab-a0ff-d0ad422ab612.gif" alt="">
          </div>
          <div class="prim-rack--wrapper">
            <!-- Next to main img -->
          </div>
        </div>
      </div>
    </section>

    <section>
      <div class="container">
        <div class="grid-golden-ratio">
          <div>

            <section>
              <div class="heading">
                <h1>Byt&nbsp;D64</h1>
                <span class="status status--available dot">Volný</span>
                <div class="actions">
                  <div class="action"><a href="#hypo"><i class="fa-light fa-calculator"></i></a></div>
                  <div class="action fav"><i class="fal fa-heart"></i></div>
                </div>
              </div>
              <h2 class=""><a href="#">Rezidence Basilejské náměstí</a><span>Praha&nbsp;3 &#8209; Žižkov</span></h2>
              <div class="price">
                <strong>4.796.113&nbsp;Kč</strong>
                <!-- <p class="stealth">Všechny ceny jsou uváděny včetně DPH.</p> -->
              </div>
            </section>

            <section>
              <div class="p-infos separators cardd">
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
            </section>

            <!-- <section>
              <h3>Ke stažení</h3>
              <div class="buttons-holder">
                <a href="#" class="btn btn-gray inline">Karta bytu<i class="fa-regular fa-file-pdf"></i></a>
                <a href="#" class="btn btn-gray inline">Technický půdorys<i class="fa-regular fa-file-pdf"></i></a>
                <a href="#" class="btn btn-gray inline">Detail bytu<i class="fa-regular fa-file-pdf"></i></a>
              </div>
            </section> -->

            <section>
              <div>
                <a href="#" class="smol-link">Karta bytu<i class="fa-regular fa-file-pdf"></i></a>
                <a href="#" class="smol-link">Technický půdorys<i class="fa-regular fa-file-pdf"></i></a>
                <a href="#" class="smol-link">Detail bytu<i class="fa-regular fa-file-pdf"></i></a>
              </div>
            </section>

            <section>
            <h3>Základní informace</h3>
              <SpecsTable1 />
            </section>

            <section>
              <h3>Místnosti</h3>
               <SpecsTable2 />
            </section>

            <section>
              <h3>Příslušenství</h3>
              <div class="specs-table apart ">
                <table>
                  <tbody>
                    <tr>
                      <td>Sklep/y</td>
                      <td><a href="#">PP2 / S123</a></td>
                      <td>6,2&nbsp;m²</td>
                    </tr>
                    <tr>
                      <td>Dvougarážové uzavřené stání</td>
                      <td><a href="#">PP2&nbsp;/&nbsp;2G100</a></td>
                      <td></td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </section>

            <section>
              <h3>Speciální vybavení</h3>
              <div class="amenities">
                <PInfo>
                  <template #icon><i class="fa-light fa-plug-circle-bolt"></i></template>
                  <template #heading>Elektropříprava pro předokenní žaluzie</template>
                </PInfo>
                <PInfo>
                  <template #icon><i class="fa-light fa-air-conditioner"></i></template>
                  <template #heading>Klimatizace</template>
                </PInfo>
                <PInfo>
                  <template #icon><i class="fa-light fa-blinds"></i></template>
                  <template #heading>Předokenní žaluzie</template>
                </PInfo>
                <PInfo>
                  <template #icon><i class="fa-light fa-shield-check"></i></template>
                  <template #heading>Zabezpečovací zařízení</template>
                </PInfo>
                <PInfo>
                  <template #icon><i class="fa-light fa-fan"></i></template>
                  <template #heading>Rekuperace</template>
                </PInfo>
                <PInfo>
                  <template #icon><i class="fa-light fa-door-closed"></i></template>
                  <template #heading>Výběr provedení podlah a dveří podle Vašich představ</template>
                </PInfo>
              </div>
            </section>

             <section id="hypo">
               <h3>Hypoteční kalkulačka</h3>
              <div class="cardd">
                <p>chcete vědět jak dlouho budete platit tenhle 0+kk? CELEJ ŽIVOT! tak dlouho! nebudete mít na chleba páč budete platit 107% svý měsíční výplaty jen za tenhle bejvák. budete mít dvě práce abyste ho mohli splácet a i to bude málo.</p>
              </div>
             </section>

          </div>
          <!-- End of left column -->
          <aside class="desktop-only">
              <div class="cardd">
              <p>Kontaktujte nás</p>
              <div>
                <a href="#" class="btn btn-gray">Něco</a>
                <!-- <span>nebo</span> -->
                <a href="#" class="btn btn-yellow">Rezervovat</a>
              </div>
              <hr>
              <span>Další možnosti, kontakt form, adresa CG, otevírací doby, telefon, whatever</span>
            </div>
            <p class="stealth">Všechny ceny jsou uváděny včetně DPH.</p>
          </aside>
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

    <aside class="mobile-only">
      <div class="cardd thin">
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

  section:not(:first-child, :last-child){
    margin-block: 1.5rem;
  }

  img{
    object-fit: cover;
  }

  @media screen and (max-width: 991px){
    .desktop-only{
      display: none;
    }
  }

  @media screen and (min-width: 992px){
    .mobile-only{
      display: none;
    }
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
    gap: 0.75rem;
    /* line-height: 1; */
    /* margin-bottom: 0.5rem; */
    flex-wrap: wrap;
  }

  :is(h1, h2, h3, h4, h5, h6):first-child{
    /* margin-top: 0; */
    /* color: red; */
  }

  h1{
    font-size: 2rem;
    font-weight: 700;
  }

  h2{
    font-size: 1rem;
    margin: 0;
    font-weight: 400;
    display: inline-flex;
    flex-direction: column;
    line-height: 1.4;
    /* margin-bottom: 0.5rem; */
  }

  h2 > *+*::before{
    /* content: '|'; */
    /* content: '•'; */
    margin: 0 0.5em;
    opacity: 0.5;
    
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
  

  .price{
    font-size: 1.5rem;
    margin-top: 1.0rem;
    line-height: 1;
  }


  @media screen and (max-width: 991px){
    h1{
      font-size: 1.75rem;

      font-size: 22px;
    }

    .price{
      font-size: 1.375rem;

      font-size: 24px;
    }
  }


  .grid-golden-ratio{
    display: grid;
    gap: 1.25rem 2rem;
    grid-template-columns: 1fr;
    position: relative;
  }


  @media screen and (min-width: 992px) {
    .grid-golden-ratio{
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

  .prim-rack > .cardd{
    width: 100%;
    /* height: 90px; */
    /* aspect-ratio: 1; */
    /* padding: 10px; */
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

  .specs-table {
    font-size: 0.875rem;
    margin-block: -0.5rem;
  }

  .prim-in .actions{
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

  .heading .actions {
    display: flex;
    align-self: center;
    margin-left: auto;
    gap: 4px;

    position: absolute;
    top: -4px;
    right: 4px;
    flex-direction: column-reverse;
    gap: 6px;
  }

  .action{
    width:  2.5rem;
    height: 2.5rem;
    aspect-ratio: 1;
    /* background-color: rgba(0,0,0,0.5); */
    border-radius: 999px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    text-align: center;
    cursor: pointer;
    /* color: white; */
    transition: background-color 0.1s;

    /* With bg (card-style) */
    background-color: white;
    border: 1px solid #f1f1f1;
    width:  50px;
    height: 50px;
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


  .p-infos {
    /* display: flex;
    justify-content: center;
    gap: 1rem 5%;
    flex-wrap: wrap;
    justify-content: space-evenly;
    margin-block: 0.5rem; */
    /* align-items: baseline; */
    

    /* Proportional grid */
    display: grid;
    grid-auto-flow: column;
    width: 100%;
    margin: 0;
    padding-inline: 0;
  }

  .p-infos.separators{
      .p-info{
        justify-content: center;
        padding: 0 0.5rem;
      }
  }

  @media screen and (min-width: 992px) {
    .p-infos.separators .p-info+.p-info {
      border-left: 1px solid var(--color-gray-mid);
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
    opacity: 50%;

    aside & {
      margin: 0.5rem 0;  
    }
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
  }

  aside{
    text-align: center;
    line-height: 1.25;
  }

  aside.desktop-only{
    position: sticky;
    top: 16px;
    /* Sticky header */
    top: calc(var(--header-height) + 16px);
  }

  h5{
    font-size: 1rem;
    color: var(--color-blue, #20234c);
    margin-bottom: 1rem;
    text-align: center;
  }

  aside .btn {
    margin-block: 0.75rem;
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

  .amenities{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem 1rem;
    /* padding: 0.5rem 0; */
  }

  .smol-link{
    text-decoration: none;
    display: inline-flex;
    align-self: center;
    gap: 8px;
    margin-right: 8px;
    flex-direction: row-reverse;
    line-height: 1;

    &:hover{
      text-decoration: underline;
    }
  }

</style>