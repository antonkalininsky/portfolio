<script setup lang="ts">
import { ref } from 'vue';
import BioComponent from './components/BioComponent.vue';
import ExperienceComponent from './components/ExperienceComponent.vue';
import DemoComponent from './components/DemoComponent.vue';

const navMap = {
  BioComponent,
  ExperienceComponent,
  DemoComponent
}

const navKey = ref('BioComponent')

const navItems = [
  {
    title: 'Bio',
    key: 'BioComponent'
  },
  {
    title: 'Experience',
    key: 'ExperienceComponent'
  },
  {
    title: 'Demo',
    key: 'DemoComponent'
  }
]

</script>

<template>
  <div class="main">
    <div class="main__column">
      <div class="header">
        <div class="header__name">
          Polosin Anton
        </div>
        <div class="header__subname">
          frontend developer
        </div>
      </div>
      <div class="navigation">
        <div
          v-for="item in navItems"
          :key="item.key"
          @click="() => navKey = item.key"
          class="navigation__item"
        >
          {{ item.title }}
        </div>
      </div>
    </div>
    <div class="main__column">
      <component
        :is="navMap[navKey]"
      />
    </div>
  </div>
</template>

<style scoped>
.main {
  display: grid;
  grid-template-columns: auto auto;
  column-gap: 20px;
  border: 1px solid red;
  padding: 2rem;
}

.header {
  margin-bottom: 20px;
}

.header__name {
  white-space: nowrap;
}

.header__subname {
  white-space: nowrap;
}

.navigation__item {
  cursor: pointer;
}

.navigation__item:hover {
  text-decoration: underline;
}
</style>
