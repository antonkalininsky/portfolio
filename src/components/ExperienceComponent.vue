<script setup lang="ts">
const expItems = [
    {
        dates: "май 2022 - май 2023",
        workplace: "КТ КОМПЛЕКС",
        description: "Разработка ПО в рамках грантов и научных проектов.",
        projects: [
            {
                title: "Проект: разработка MES системы для производства.",
                points: [
                    "разрабатывал веб интерфейс, взаимодействие с бэком, различные виды представления данных",
                    "реализовывал различные уровни доступа для пользователей",
                    "для демонстрационных целей мокал серверные запросы",
                    "выполнял функции тимлида, имел в подчинении верстальщика"
                ],
                stack: "Стек: vue3, vue-router, vuex, chartjs"
            }
        ]
    },
    {
        dates: "май 2023 - июль 2023",
        workplace: "жандосов софт",
        description: "Стартап",
        projects: [
            {
                title: "Проект: мобильное приложение такси.",
                points: [
                    "разрабатывал интефрейс заказа такси и отлаживал взаимодействие с сервером",
                    "решал задачу восстановления состояния приложения после закрытия",
                    "подключал карту 2gis и реализовывал функционал отображения позиции клиента, такси и построения пути"
                ],
                stack: "Стек: vue3, vue-rotuer, vuetify, pinia, 2gis API"
            },
            {
                title: "Проект: CRM для тренажерного зала.",
                points: [
                    "реализовывал новый функционал",
                    "рефакторил кодовую базу, внедрил модульную архитектуру",
                    "писал тесты для API"
                ],
                stack: "Стек: vue3, vue-rotuer, vuetify, vuex, jest"
            },
        ]
    },
    {
        dates: "июль 2023 - нв",
        workplace: "Аврора Холдинг",
        description: "Продуктовая разработка",
        projects: [
            {
                title: "Проект: ERP для производства.",
                points: [
                    "Решал проблемы производительности у клиента при работе с большими проектами, оптимизировал алгоритмы, отрисовку, серверные запросы. Добился многократного прироста производительности.",
                    "Внедрял новый межмодульный функционал формы с многократной вложенностью и валидацией",
                    "дорабатывал ui kit",
                    "рефакторил кодовую базу",
                    "участвовал в принятии архитектурных решений"
                ],
                stack: "Стек: nuxt2, vuex, buefy, tailwindcss, sass"
            }
        ]
    },
]

</script>
<template>
  <div>
    <div
        v-for="item in expItems"
        :key="item.workplace"
        class="work-item"
    >
        <div class="work-item__header">
            <div>
                {{ item.dates }}
            </div>
            <div>
                {{ item.workplace }}
            </div>
        </div>
        <div class="work-item__subheader">
            {{ item.description }}
        </div>
        <div
            v-for="projectItem in item.projects"
            :key="projectItem.title"
            class="work-item__body"
        >
            <div class="work-list">
                <div class="work-list__header">
                    {{ projectItem.title }}
                </div>
                <ul class="work-list__body">
                    <li
                        v-for="point in projectItem.points"
                        :key="point"
                        class="work-list__item"
                    >
                        {{ point }}
                    </li>
                </ul>
                <div class="work-item__footer">
                    {{ projectItem.stack }}
                </div>
            </div>
        </div>
    </div>





  </div>
</template>
<style scoped>
.work-item {
    border-bottom: 1px solid black;
    margin-bottom: 20px;
}

.work-item__body {
    margin-block: 15px;
}
</style>