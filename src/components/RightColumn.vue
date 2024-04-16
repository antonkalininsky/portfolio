<script setup>
const experience = [
  {
    title: 'ООО Аврора Холдинг',
    description: 'Продуктовая разработка',
    dates: '2023 - Н.В.',
    projects: [
      {
        title: 'ERP для производства',
        points: [
          'решал оптимизационные проблемы с точки зрения алгоритмов, отрисовки и серверных запросов; добился многократного прироста производительности',
          'реализовывал сложную бизнес-логику на стороне клиента',
          'дорабатывал ui kit',
          'рефакторил кодовую базу, провел декомпозицию, применял DRY',
          'участвовал в принятии архитектурных решений',
          'подключал серверные запросы и участвовал в проектировании API'
        ],
        stack: ['Nuxt2', 'Vuex', 'Axios', 'Buefy', 'TailwindCss', 'Sass']
      }
    ]
  },
  {
    title: 'ТОО Dzhandosov Soft',
    description: 'Стартап',
    dates: 'Май - Июль 2023',
    projects: [
      {
        title: 'Мобильное приложение такси',
        points: [
          'разрабатывал интерфейс заказа такси',
          'решал задачу восстановления состояния после закрытия приложения',
          'подключал карту 2gis и реализовывал функционал отображения позиции клиента и построения пути'
        ],
        stack: ['Vue3', 'Vue-Router', 'Pinia', 'Vuetify', 'Axios', '2gis API']
      },
      {
        title: 'CRM для тренажерного зала',
        points: [
          'реализовывал интерфейсы для создания и управления аккаунтами посетителей, аккаунтами тренеров, абонементами и групповыми занятиями',
          'реализовывал интерфейс регистрации посещений тренажерного зала',
          'реализовывал дашборд для отдела продаж',
          'рефакторил кодовую базу, внедрил модульную архитектуру',
          'писал тесты для серверных запросов',
          'подключал серверные запросы и участвовал в проектировании API'
        ],
        stack: ['Vue3', 'Vue-Router', 'Vuex', 'Vuetify', 'Axios', 'Jest']
      }
    ]
  },
  {
    title: 'ООО КТ Комплекс',
    description: 'Разработка по гранту',
    dates: '2022 - 2023',
    projects: [
      {
        title: 'MES система для производства',
        points: [
          'разрабатывал веб интерфейс с различными формами отображения информации: графики, таблицы, блок-схемы',
          'реализовывал авторизацию и различные уровни доступа для пользователей',
          'занимался менторством, проводил код ревью'
        ],
        stack: ['Vue3', 'Vue-Router', 'Vuex', 'Chart-js']
      }
    ]
  }
]

const petProjects = ['Шахматы', 'Верстка', 'Музыка']
</script>
<template>
  <!-- right column -->
  <div class="content">
    <!-- about -->
    <section class="section">
      Привет! Я - фронтенд разработчик с сильными софт скилами. Ценю качественный код и отлаженные
      рабочие процессы, готов участвовать в организации работы. Стремлюсь к постоянному
      профессиональному развитию, не боюсь сложных задач.
    </section>
    <!-- experience -->
    <section class="section">
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
    <section class="section">
      <div>Проекты</div>
      <ul>
        <li v-for="item in petProjects" :key="item">{{ item }}</li>
      </ul>
    </section>
  </div>
</template>
<style scoped>
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
  background-color: var(--vt-c-divider-light-1);
}
</style>
