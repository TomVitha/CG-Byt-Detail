<script setup>
  
</script>

<template>
  <div class="timeline">
    <div class="timeline__content">
      <slot></slot>
    </div>
  </div>
</template>

<style>
  /* ? TIMELINE ? */
/** tohle je celý clusterfuck **/

.timeline{
    --tl-dot-size: 36px;
    --tl-line-size: 3px;
    --tl-dots-gap: 1.75rem;
    --tl-dot-line-gap: 12px;
    margin: 2rem 0 2rem;
}

.timeline__content{
    display: grid;
    grid-auto-flow: column;
    grid-auto-columns: 1fr;
    width: 100%;
    align-items: baseline;
    justify-items: center;
}

.timeline__point{
    text-align: center;
    position: relative;
    width: 100%;
    /* width: fit-content; */
}

.timeline__point__name{
    line-height: 1.1;
    cursor: pointer;
    max-width: 200px;
    padding: 4px;
    position: relative;
    margin: 0 auto;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0.0);
    display: grid;
    grid-auto-flow: row;
    gap: 0.5rem 1rem;
}

/** Timeline Point Dot **/
.timeline__point__name::before{
    position: static;
    transform: none !important;
    /* Hollow circle */
    content: "\f111";
    /* Info - (i) in circle */
    content: "\f05a";

    font-family: "Font Awesome 6 Pro";
    font-weight: 400;
    font-weight: 300;
    font-size: var(--tl-dot-size);
    color: #cccccc;
    width: var(--tl-dot-size);
    width: -moz-fit-content;
    width: fit-content;
    margin: 0 auto;
}

/** Connecting Line **/
.timeline__point:not(:last-child)::after{
    content: '';
    display: block;
    height: var(--tl-line-size);
    background: #cccccc;
    position: absolute;
    width: calc(100% - var(--tl-dot-size) - var(--tl-dot-line-gap) );
    z-index: -1;
    top: calc( (var(--tl-dot-size) / 2) + 4px);
    left: calc(50% + (var(--tl-dot-size) / 2) + (var(--tl-dot-line-gap) / 2));
    z-index: 1;
}

/** Description flyout styling - fallback for Tippy **/
.timeline__point__description{
    color: white;
    background: #7281a3;
    font-size: 14px;
    padding: 0.5rem;
    border-radius: 4px;
    line-height: 1.333;
    position: absolute;
    bottom: calc(100% + (var(--tl-dot-size) / 2) );
    width: 250px;
    left: 50%;
    transform: translate(-50%, 5%);
    z-index: 3;
    cursor: default;
    opacity: 0;
    visibility: hidden;
    -webkit-user-select: none;
    user-select: none;
    transition: transform 200ms, opacity 200ms, visibility 0ms 200ms;

    /* Hidden by default */
    /* display: none; */
}

.timeline.no-tippy .timeline__point__description{
    display: block;
}

/** Description flyout arrow **/
.timeline__point__description::before{
    content: '';
    display: block;
    width: 10px;
    height: 10px;
    aspect-ratio: 1/1;
    background: #7281a3;
    position: absolute;
    left: 50%;
    bottom: 0%;
    transform: translate(-50%, 50%) rotate(45deg);
    transform-origin: center;
    z-index: -1;
}


/** Dot fill on hover **/
.timeline__point__name:hover::before{
    /* background: #cccccc; */
    /* font-weight: 400;
    content: "\f192"; */
}


/* ? Done point */
.timeline__point.done{
    color: var(--color-primary, var(--color-blue, #20234c));
}
.timeline__point.done .timeline__point__name::before{
    /* Check mark */
    content: "\f058";
    font-weight: 900;
    color: currentColor;
}
.timeline__point.done:not(:last-child)::after{
    background: currentColor;
}

/* ? Active point */
.timeline__point.current{
    color: var(--color-primary, var(--color-blue, #20234c));
}
.timeline__point.current .timeline__point__name::before{
    content: "\f192";
    font-weight: 400;
    color: currentColor;
}
.timeline__point.current .timeline__point__name:hover::before{
    font-weight: 900;
}
.timeline__point.current:not(:last-child)::after{
    /* background: currentColor; */
}


/** Show description **/
/** When hover over Name, Dot or Description **/
.timeline__point__name:hover~.timeline__point__description,
.timeline__point__description:hover{
    opacity: 1;
    visibility: visible;
    /* -webkit-user-select: auto; */
    /* user-select: auto; */

    transform: translate(-50%, 0%);
    transition: transform 200ms, opacity 200ms, visibility 0ms 0ms;
}

/** Switch to VERTICAL **/
@media screen and (max-width: 767px){
    .timeline{
        --tl-dot-line-gap: 2px;
    }
    .timeline__content{
        display: flex;
        flex-direction: column;
        gap: var(--tl-dots-gap);
        padding: 0;
        padding-left: 10%;
    }

    .timeline__point{
        width: -moz-fit-content;
        width: fit-content;
    }

    .timeline__point__name{
        display: flex;
        align-items: center;
        flex-direction: row;
        gap: 1rem;

        text-align: left;
        vertical-align: middle;
        margin: 0;
        max-width: none;
        padding: 0;
    }

    /** Dot **/
    .timeline__point__name::before{
        position: static;
        margin: 0;
        transform: none;
    }

    /** Connecting Line **/
    .timeline__point:not(:last-child)::after{
        width: var(--tl-line-size);
        height: calc(var(--tl-dots-gap) - var(--tl-dot-line-gap));
        top: calc(100% + (var(--tl-dot-line-gap) / 2) );
        left: calc(var(--tl-dot-size) / 2);
        bottom: unset;
        transform: translate(-50%, -0%);
    }

    .timeline__point__description{
        transform: translate(50%, calc(-50% - var(--tl-dot-size) / 2));
        bottom: unset;
    }

    .timeline__point__name:hover~.timeline__point__description, 
    .timeline__point__description:hover{
        transform: translate(calc(50% + 1.5rem), calc(-50% - var(--tl-dot-size) / 2));
    }

    .timeline__point__description::before{
        bottom: unset;
        left: 0;
        top: 50%;
        transform: translate(-50%, -50%) rotate(45deg);
    }
}

@media screen and (max-width: 575px){
    .timeline__point__description{
        transform: translate(-50%, 0%);
        bottom: 100%;
    }
    .timeline__point__description::before{
        bottom: 0;
        left: 50%;
        top: unset;
        transform: translate(-50%, 45%) rotate(45deg);
    }
    .timeline__point__name:hover~.timeline__point__description, 
    .timeline__point__description:hover{
        transform: translate(-50%, -1.5rem);
    }
}

@media screen and (max-width: 399px){

    .timeline__point__description{
        left: -10%;
        transform: none;
        max-width: 90vw;
    }

    .timeline__point__name:hover~.timeline__point__description, 
    .timeline__point__description:hover{
        transform: translate(0, -1.5rem);
    }

    .timeline__point__description::before{
        left: 50%;
        transform: translate(-50%, 50%) rotate(45deg);
    }
}


/** Font Awesome icons **/
.timeline i[class^="fa-"]{
    margin: 0 0.25em;
    font-size: 0.8em;
}

/* * Hides (i) icon within text */
.timeline i.fa-circle-info{
    display: none;
}

/* ? TIMELINE (end) ? */
</style>