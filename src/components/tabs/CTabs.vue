<script setup>
import { ref, provide, defineProps, defineSlots, computed } from 'vue'

const props = defineProps({
  class: {
    type: String,
    default: 'line'
  }
})
const slots = defineSlots()
const tabTitles = ref(slots.default().map((tab) => ({ 
  title: tab.props.title, 
  class: tab.props.class || 'tab',
  component: tab
})))
const selectedTitle = ref(tabTitles.value[0].title)

provide("selectedTitle", selectedTitle)

const selectedTab = computed(() => {
  return tabTitles.value.find(tab => tab.title === selectedTitle.value)?.component
})
</script>

<template>
  <!-- Tabs (container) -->
  <!-- Permanent class .tabs + optional styling class -->
  <div :class="['tabs', props.class]">
    <!-- Tab -->
    <button 
      :class="[
        tab.class, 
        { active: tab.title === selectedTitle }
      ]"
      v-for="tab in tabTitles" 
      :key="tab.title" 
      :title="tab.title"
      @click="selectedTitle = tab.title"
    >
      {{ tab.title }}
    </button>
  </div>
  <!-- Content of tab -->
  <component :is="selectedTab" />
</template>

<style scoped>

</style>