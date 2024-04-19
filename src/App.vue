<script setup>
import { ref, computed } from 'vue'
import RightColumn from './components/RightColumn.vue'
import { links } from './data/links'
import { navItems } from './data/navItems'
import SvgIcon from '@jamescoyle/vue-icon'

const rightColumn = ref()
const scrollPosition = ref()

const navStyling = computed(() => {
  let aboutSection = false, // 0
    experienceSection = false, // 458
    projectSection = false // 1348
  if (scrollPosition.value >= 0 && scrollPosition.value < 300) {
    aboutSection = true
  }
  if (scrollPosition.value >= 300 && scrollPosition.value < 1000) {
    experienceSection = true
  }
  if (scrollPosition.value >= 1000) {
    projectSection = true
  }
  return {
    aboutSection,
    experienceSection,
    projectSection
  }
})

init()

function init() {
  scrollPosition.value = Math.round(document.documentElement.scrollTop || document.body.scrollTop)
  window.addEventListener('scroll', () => scrollPosition.value = Math.round(document.documentElement.scrollTop || document.body.scrollTop))
}

function handleNavigation(key) {
  rightColumn.value.scrollToSection(key)
}
</script>

<template>
  <div class="main">
    <!-- left column -->
    <div class="face">
      <div>
        <!-- face -->
        <h1>Полосин Антон</h1>
        <div class="subheader">Frontend разработчик</div>
        <!-- nav -->
        <nav class="nav">
          <ul class="nav__body">
            <li
              class="nav__item"
              :class="{ active: navStyling[item.key] }"
              v-for="item in navItems"
              :key="item.title"
              @click="handleNavigation(item.key)"
            >
              {{ item.title }}
            </li>
          </ul>
        </nav>
      </div>
      <div class="face__footer">
        <!-- links -->
        <div
          class="link"
          v-for="link in links"
          :key="link.title"
        >
          <svg-icon type="mdi" :path="link.icon" />
          <div class="link__title">
            {{ link.title }}
          </div>
        </div>
      </div>
    </div>
    <RightColumn ref="rightColumn" />
  </div>
</template>

<style scoped>
.link {
  cursor: pointer;
  display: grid;
  grid-template-columns: min-content 25% auto;
  column-gap: 10px;
  margin-bottom: 10px;
}

.link:hover {
  text-decoration: underline;
}

h1 {
  line-height: 3rem;
  font-size: 3rem;
  font-weight: 700;
}

.subheader {
  line-height: 3rem;
  font-size: 1.5rem;
  font-weight: 500;
}

.nav {
  padding-top: 4rem;
}

.nav__body {
  list-style-type: none;
  padding: 0;
}

.nav__item {
  cursor: pointer;
  margin-bottom: 1.6rem;
  width: fit-content;
  position: relative;
  font-weight: 500;
}

.nav__item::after {
  content: '';
  display: block;
  position: absolute;
  left: 0px;
  bottom: 0;
  width: 0;
  height: 2px;
  background-color: var(--color-text);
  opacity: 0.3;
  transition: 0.3s;
}

.nav__item:hover.nav__item::after {
  width: 100%;
}

.nav__item.active.nav__item::after {
  opacity: 0.8;
  width: 100%;
}

.main {
  display: grid;
  grid-template-columns: 0.5fr 1fr;
  column-gap: 50px;
}

.face {
  padding: 5rem 0;
  position: sticky;
  height: calc(100vh - 5rem);
  top: 0;
}

.face__footer {
  position: absolute;
  bottom: 0;
}
</style>
