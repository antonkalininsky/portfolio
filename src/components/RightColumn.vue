<script setup>
import { petProjects } from '@/data/petProjects'
import { experience } from '@/data/experience'
import { ref } from 'vue'
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiArrowTopRight } from '@mdi/js'

const aboutSection = ref()
const experienceSection = ref()
const projectSection = ref()

function scrollToSection(key) {
  this.$refs[key].scrollIntoView({ behavior: 'smooth', block: 'start' })
}

defineExpose({
  scrollToSection
})
</script>
<template>
  <!-- right column -->
  <div class="content">
    <!-- about -->
    <section class="section">
      <div class="section__marker" ref="aboutSection"></div>
      <div class="section__header">Обо мне</div>
      <div class="about-me">
        Привет! Я - фронтенд разработчик с сильными софт скилами. Это моя персональная страница, тут вы можете найти подробную информацию о моей профессиональной деятельности, также можете <a class="download" href="/polosin_frontend_cv.pdf" download>скачать моё резюме в формате PDF</a>.
      </div>
      <div class="about-me">
        Мой опыт фронтенд разработки 2 года, основной фреймворк - Vue. Я ценю качественный код и отлаженные рабочие процессы. Стремлюсь к постоянному профессиональному развитию, не боюсь сложных задач.
      </div>
    </section>
    <!-- experience -->
    <section class="section">
      <div class="section__marker" ref="experienceSection"></div>
      <div class="section__header">Опыт</div>
      <div v-for="expItem in experience" :key="expItem.title" class="exp-item">
        <div class="exp-item__dates">
          {{ expItem.dates }}
        </div>
        <div class="exp-item__header">
          <div class="exp-item__country">
            {{ expItem.country }}
          </div>
          <div class="exp-item__title">
            {{ expItem.title }}
          </div>
          <div class="exp-item__description">
            {{ expItem.description }}
          </div>
        </div>
        <template v-for="project in expItem.projects" :key="project.title">
          <div></div>
          <div class="exp-item__project">
            <div>
              {{ project.title }}
            </div>
            <ul class="nav__body">
              <li class="nav__item" v-for="point in project.points" :key="point">{{ point }}</li>
            </ul>
            <div class="bubble-box">
              <span class="bubble" v-for="item in project.stack" :key="item">
                {{ item }}
              </span>
            </div>
          </div>
        </template>
      </div>
    </section>
    <!-- projects -->
    <section class="section">
      <div class="section__marker" ref="projectSection"></div>
      <div class="section__header">Проекты</div>
      <div class="pet">
        <div class="pet-item" v-for="petItem in petProjects" :key="petItem.title">
          <div class="pet-item__header">
            <svg-icon type="mdi" :path="petItem.icon" size="50" />
            <div class="pet-item__title">
              {{ petItem.title }}
            </div>
          </div>
          <div class="pet-item__body">
            {{ petItem.description }}
          </div>
          <div class="pet-item__links" v-if="petItem?.links">
            <a
              class="pet-item__link link"
              :href="petItem.links.demo"
              target="_blank"
            >
              <div class="link__title">
                Демо
              </div>
              <svg-icon
                class="link__icon"
                type="mdi"
                :path="mdiArrowTopRight"
                size="16"
              />
            </a>
            <a
              class="pet-item__link link"
              :href="petItem.links.source"
              target="_blank"
            >
              <div class="link__title">
                Исходники
              </div>
              <svg-icon
                class="link__icon"
                type="mdi"
                :path="mdiArrowTopRight"
                size="16"
              />
            </a>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<style scoped>
.download {
  text-decoration: underline;
  opacity: 0.6;
  transition: 0.2s;
  color: rgb(var(--color-text));
}

.download:hover {
  opacity: 1;
}

.link {
  color: var(--color-text);
  position: relative;
  width: min-content;
  opacity: 0.7;
  transition: 0.1s;
}

.link__title {
  font-weight: 500;
}

.link:hover {
  opacity: 1;
}

.link:active {
  text-decoration: underline;
  text-decoration-thickness: 1.5px;
  text-underline-offset: 5px;
}

.link__icon {
  position: absolute;
  top: 5px;
  right: -16px;
  transition: 0.1s;
}

.link:hover .link__icon {
  top: 3px;
  right: -20px;
}

.pet-item {
  margin-bottom: 3rem;
}

.pet-item__header {
  display: grid;
  grid-template-columns: min-content auto;
  column-gap: 1rem;
  align-items: center;
  margin-bottom: 1rem;
}

.pet-item__body {
  margin-bottom: 0.5rem;
  line-height: clamp(1.4rem, 5vw, 1.6rem);
}

.pet-item__links {
  width: 30%;
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.pet-item__link {
  cursor: pointer;
}

.pet-item__title {
  font-size: clamp(1.1rem, 2vw, 1.3rem);
  font-weight: 500;
}

.content {
  padding: 5rem 0;
}

.exp-item {
  margin-bottom: 40px;
  display: grid;
  grid-template-columns: 0.3fr 1fr;
  line-height: clamp(1.4rem, 5vw, 1.6rem);
}

.exp-item:last-child {
  margin-bottom: 0;
}

.exp-item__header {
  font-weight: 500;
  margin-bottom: 1rem;
  display: flex;
  flex-wrap: wrap;
  column-gap: 1rem;
}

.exp-item__description {
  opacity: 0.6;
  font-weight: initial;
}

.exp-item__dates {
  opacity: 0.6;
}

.exp-item__project {
  margin-bottom: 20px;
}

.nav {
  padding-top: 4rem;
}

.nav__body {
  padding-left: 1rem;
  padding-bottom: 1rem;
}

.nav__item {
  width: fit-content;
}

.bubble-box {
  display: flex;
  flex-wrap: wrap;
}

.bubble {
  padding: 0.3rem 0.6rem;
  margin-inline: 0.2rem;
  margin-bottom: 0.2rem;
  border-radius: 1rem;
  font-weight: 600;
  background-color: var(--vt-c-light-blue);
  color: var(--vt-c-white-soft);
  white-space: nowrap;
  font-size: clamp(0.8rem, 2vw, 1rem);
}

.section__header {
  display: none;
  position: relative;
  font-weight: 500;
  font-size: 1.2rem;
  margin-bottom: clamp(0.5rem, 2vw, 1rem);
}

.about-me {
  margin-bottom: 10px;
  line-height: clamp(1.4rem, 5vw, 1.6rem);
}

@media screen and (max-width: 1024px) {
  .content {
    padding: 0;
  }

  .section__header {
    display: block;
  }
}

@media screen and (max-width: 768px) {
  .exp-item {
    display: block;
  }
}
</style>
