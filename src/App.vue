<script setup>
import { ref } from 'vue'
import RightColumn from '@/components/RightColumn.vue'
import LeftColumn from '@/components/LeftColumn.vue'

const rightColumn = ref()

function handleNavigation(key) {
  rightColumn.value.scrollToSection(key)
}
</script>

<template>
  <div class="main">
    <LeftColumn @scroll="handleNavigation" />
    <RightColumn ref="rightColumn" />
  </div>
</template>

<style scoped>
.main {
  display: grid;
  grid-template-columns: 0.5fr 1fr;
  column-gap: 50px;
}

@media screen and (max-width: 1024px) {
  .main {
    display: block;
    grid-template-columns: unset;
    column-gap: unset;
  }
}
</style>
