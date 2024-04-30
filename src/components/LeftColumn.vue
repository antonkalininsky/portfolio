<script setup>
import { ref, computed } from 'vue'
import { links } from '@/data/links'
import { navItems } from '@/data/navItems'
import SvgIcon from '@jamescoyle/vue-icon'

const scrollPosition = ref()

const navStyling = computed(() => {
  let aboutSection = false,
    experienceSection = false,
    projectSection = false
  if (scrollPosition.value >= 0 && scrollPosition.value < 300) {
    aboutSection = true
  }
  if (scrollPosition.value >= 300 && scrollPosition.value < 1700) {
    experienceSection = true
  }
  if (scrollPosition.value >= 1700) {
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

function handleLinkClick(link) {
  if (link?.isMail) {
    window.open(`mailto:${link.url}`)
  } else {
    const a = document.createElement('a')
    a.target = '_blank'
    a.href = link.url
    a.click()
  }
}
</script>
<template>
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
              @click="$emit('scroll', item.key)"
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
          v-tippy="{
            content: link.title,
            delay: [500, null]
          }"
          @click="handleLinkClick(link)"
        >
          <svg-icon
            class="link__icon"
            type="mdi"
            :path="link.icon"
            size="30"
          />
        </div>
      </div>
    </div>
</template>
<style scoped>
.link {
  display: flex;
  justify-content: center;
  align-items: center;
}

.link__icon {
  opacity: 0.7;
  cursor: pointer;
  transition: 0.2s;
}

.link__icon:hover {
  transform: scale(1.2);
  opacity: 1;
}

h1 {
  line-height: 3rem;
  font-size: clamp(2rem, 10vw, 3rem);
  font-weight: 700;
}

.subheader {
  line-height: clamp(2rem, 9vw, 3rem);
  font-size: clamp(1rem, 5vw, 1.5rem);
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

.face {
  padding: 5rem 0;
  position: sticky;
  height: calc(100vh - 5rem);
  min-height: 500px;
  top: 0;
}

.face__footer {
  position: absolute;
  bottom: 0;
  width: 50%;
  display: grid;
  grid-template-columns: 25% 25% 25% 25%;
  column-gap: 20px;
  justify-items: flex-start;
}

@media screen and (max-width: 1024px) {
  .face {
    padding: clamp(1rem, 5vw, 3rem) 0 5rem 0;
    position: relative;
    height: auto;
    width: 100%;
    min-height: 0;
  }

  .face__footer {
    display: flex;
    bottom: 2rem;
    width: 50%;
  }

  .nav {
    display: none;
  }

  .link__icon {
    opacity: 1;
    transition: unset;
  }

  .link__icon:hover {
    transform: unset;
  }
}
</style>