<script setup>
import RightColumn from './components/RightColumn.vue'

const navItems = [
  {
    title: 'Обо мне',
    key: 'about'
  },
  {
    title: 'Опыт',
    key: 'experience'
  },
  {
    title: 'Проекты',
    key: 'projects'
  }
]

const links = [
  {
    title: 'gitHub',
    url: 'google.com'
  },
  {
    title: 'gitHub',
    url: 'google.com'
  },
  {
    title: 'gitHub',
    url: 'google.com'
  }
]

function handleNavigation(key) {
  console.log('todo', key)
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
        <span v-for="link in links" :key="link.title">{{ link.title + ' ' }}</span>
      </div>
    </div>
    <RightColumn />
  </div>
</template>

<style scoped>
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
  margin-bottom: 20px;
  width: fit-content;
}

.nav__item:hover {
  text-decoration: underline;
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
