<script setup>
    import { ref } from 'vue'
    import SpecsTable1 from '../../components/SpecsTable1.vue'
    import SpecsTable2 from '../../components/SpecsTable2.vue'

    // Help
    // const count = ref(0);
    const tabs = ref([SpecsTable1, SpecsTable2]);
    
    const selectedComp = ref(SpecsTable1) // default value
</script>

<!-- # OLD  -->

<template>
    <div class="tabs pill">
        <!-- <button @click="count++">You clicked me {{ count }} times.</button> -->
        
        <!-- Hard-coded (should be dynamically looped) -->
        <!-- conditional styling not working ffs -->
        <button @click="selectedComp = SpecsTable1" :class="['tab', { active: selectedComp === SpecsTable1 }]">Tady je Jednička</button>
        <button @click="selectedComp = SpecsTable2" :class="['tab', { active: selectedComp === SpecsTable2 }]">no a zde 2</button>

        <!-- selectedComp chce celí objekt, ale potřebujeme string pro vypsání -->
        <!-- <button
          v-for="tab in tabs"
          :key="tab"
          @click="selectedComp = tab"
          class="tab"
          :class="['tab-btn', { active: selected === tab }]"
        >
          Tab
        </button> -->
    </div>
    <!-- This component is the content itself - tables -->
    <component :is="selectedComp">
        <template #text>just kill me</template>
    </component>
</template>

<style scoped>
    
</style>