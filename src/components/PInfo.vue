<script setup>

</script>

<template>
    <div class="p-info">
        <div class="p-info--icon">
            <slot name="icon"></slot>
        </div>
        <div class="p-info--details">
            <span>
                <slot name="heading"></slot>
            </span>
            <strong>
                <slot name="text"></slot>
            </strong>
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


.p-info--details {
    display: flex;
    flex-direction: column;
    /* align-items: center; */
    gap: 0.25rem;
}

.p-info--details span {
    font-size: 0.875rem;
}

.p-info--icon{
    height: 1.875rem;
    width:  auto;
    /* aspect-ratio: 1; */
    font-size: 1.875rem;
    margin: auto;
    color: var(--color-blue);
    text-align: right;
}

@media screen and (max-width: 991px){
  .p-info{
    gap: 0.75rem;
  }

  .p-info--details{
    gap: 0.1em;
  }
  .p-info--icon{
      height: 1.5rem;
      font-size: 1.5rem;
  }
}

.p-info--icon img{
    height: 100%;
    /* width: auto; */
}

</style>