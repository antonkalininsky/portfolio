<script setup>
const experience = [
  {
    title: 'ООО КТ Комплекс',
    description: 'Грант',
    dates: '2022 - 2023',
    projects: [
      {
        title: 'MES система для производства',
        points: [
          'разрабатывал веб интерфейс с различными формами отображения информации: графики, таблицы, блок-схемы',
          'реализовывал авторизацию и различные уровни доступа для пользователей',
          'занимался менторством, проводил код ревью'
        ],
        stack: ['vue3', 'vue-router', 'vuex', 'chartjs']
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
        stack: ['vue3', 'vue-router', 'pinia', 'vuetify', 'axios', '2gis API']
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
        stack: ['vue3', 'vue-router', 'vuex', 'vuetify', 'axios', 'jest']
      }
    ]
  },
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
        stack: ['nuxt2', 'vuex', 'axios', 'buefy', 'tailwindcss', 'sass']
      }
    ]
  }
]

const navItems = [
  {
    title: 'Обо мне'
  },
  {
    title: 'Опыт'
  },
  {
    title: 'Проекты'
  }
]
</script>

<template>
  <div class="main">
    <!-- left column -->
    <div>
      <div>
        <!-- face -->
        <div>Polosin Anton</div>
        <div>frontent developer</div>
        <!-- nav -->
        <div>
          <div v-for="item in navItems" :key="item.title">{{ item.title }}</div>
        </div>
      </div>
      <div>
        <!-- links -->
        <div>links</div>
      </div>
    </div>

    <!-- right column -->
    <div>
      <!-- about -->
      <div>
        Привет! Я - фронтенд разработчик с сильными софт скилами. Ценю качественный код и отлаженные
        рабочие процессы, готов участвовать в организации работы. Стремлюсь к постоянному
        профессиональному развитию, не боюсь сложных задач.
      </div>
      <!-- experience -->
      <div>
        <div>Опыт</div>
        <div v-for="expItem in experience" :key="expItem.title" class="exp-item">
          <div class="exp-item__header">
            <div>
              {{ expItem.dates }}
            </div>
            <div>
              {{ expItem.title }}
            </div>
            <div></div>
            <div>
              {{ expItem.description }}
            </div>
          </div>
          <div>
            <div v-for="project in expItem.projects" :key="project.title" class="exp-item__project">
              <div>
                {{ project.title }}
              </div>
              <ul>
                <li v-for="point in project.points" :key="point">{{ point }}</li>
              </ul>
              <div>
                Стэк:
                <span v-for="item in project.stack" :key="item" style="padding: 5px">
                  {{ item }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- projects -->
      <div>
        <div>Проекты</div>
        <div>Шахматы</div>
        <div>Шахматы</div>
        <div>Шахматы</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.exp-item {
  margin-bottom: 40px;
}

.exp-item__header {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.exp-item__project {
  margin-bottom: 20px;
}
</style>
