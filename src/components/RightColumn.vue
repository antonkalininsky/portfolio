<script setup>
import { petProjects } from '@/data/petProjects'
import { experience } from '@/data/experience'
import { ref } from 'vue'
import SvgIcon from '@jamescoyle/vue-icon'

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
      <div style="margin-bottom: 10px">
        Привет! Я - фронтенд разработчик с сильными софт скилами. Ценю качественный код и отлаженные
        рабочие процессы, готов участвовать в организации работы. Стремлюсь к постоянному
        профессиональному развитию, не боюсь сложных задач.
      </div>
      <div style="margin-bottom: 10px">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Illum praesentium molestiae
        consequuntur mollitia, debitis rem optio necessitatibus, ullam nobis non exercitationem!
        Similique neque dolor corrupti aliquam impedit ducimus perspiciatis maxime. Lorem ipsum
        dolor sit amet consectetur adipisicing elit. Illum praesentium molestiae consequuntur
        Similique neque dolor corrupti aliquam impedit ducimus perspiciatis maxime. Lorem ipsum
        dolor sit amet consectetur adipisicing elit. Illum praesentium molestiae consequuntur
      </div>
    </section>
    <!-- experience -->
    <section class="section">
      <div class="section__marker" ref="experienceSection"></div>
      <div v-for="expItem in experience" :key="expItem.title" class="exp-item">
        <div class="exp-item__dates">
          {{ expItem.dates }}
        </div>
        <div class="exp-item__header">
          {{ expItem.title }}
          <span class="exp-item__description">
            {{ expItem.description }}
          </span>
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
            <div>
              <span class="bubble" v-for="item in project.stack" :key="item">
                {{ item }}
              </span>
            </div>
          </div>
        </template>
      </div>
    </section>
    <!-- projects -->
    <section class="section" style="margin-bottom: 1000px;">
      <div class="section__marker" ref="projectSection"></div>
      <div class="pet">
        <div class="pet-item" v-for="petItem in petProjects" :key="petItem.title">
          <svg-icon type="mdi" :path="petItem.icon" size="50" />
          <div class="pet-item__title">
            {{ petItem.title }}
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<style scoped>
.pet {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.pet-item {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  width: 10rem;
  height: 10rem;
}

.pet-item:hover {
  outline: 2px solid  var(--vt-c-light-blue)
}

.pet-item__title {
  font-size: 1.3rem;
  font-weight: 500;
}

.content {
  padding: 5rem 0;
}

.exp-item {
  margin-bottom: 40px;
  display: grid;
  grid-template-columns: 0.3fr 1fr;
}

.exp-item__header {
  font-weight: 500;
  margin-bottom: 1rem;
}

.exp-item__description {
  opacity: 0.6;
  font-weight: initial;
  margin-left: 1rem;
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
  cursor: pointer;
  width: fit-content;
}

.bubble {
  padding: 0.3rem 0.6rem;
  margin-inline: 0.2rem;
  border-radius: 1rem;
  background-color: var(--vt-c-light-blue);
  color: var(--vt-c-white-soft);
}
</style>
