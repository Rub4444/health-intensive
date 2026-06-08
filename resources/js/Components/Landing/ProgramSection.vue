<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const days = [
    {
        label: 'День 1',
        title: 'Правильное утро и ритуалы здоровья',
        summary:
            'Разберём, почему первые часы после пробуждения задают тон всему дню.',
        topics: [
            'Как начало дня влияет на следующие 12 часов',
            'Энергия: откуда она берётся и куда уходит',
            'Связь утра с настроением',
            'Как утро влияет на пищеварение',
            'Простые утренние ритуалы, которые легко повторить',
        ],
        icon: 'sunrise',
    },
    {
        label: 'День 2',
        title: 'Токсины и еда',
        summary:
            'Поговорим о продуктах, которые незаметно влияют на самочувствие, и о спокойных альтернативах.',
        topics: [
            'Глютен: что важно знать без крайностей',
            'Молочные продукты и реакция организма',
            'Сахарозаменители: где подвох',
            'Скрытые токсины в привычной еде',
            'Полезные альтернативы без фанатизма',
        ],
        icon: 'shield',
    },
    {
        label: 'День 3',
        title: 'Здоровый ЖКТ и правильное питание',
        summary:
            'Соберём всё в понятную систему питания, с которой комфортно жить каждый день.',
        topics: [
            'Вздутие и метеоризм: почему возникают',
            'Кислотность желудка простыми словами',
            'Желчеотток и его роль в пищеварении',
            'Здоровье кишечника как основа энергии',
            'Простая система питания на каждый день',
        ],
        icon: 'gut',
    },
];

const paths = {
    sunrise:
        'M3 18h18M5 18a7 7 0 0114 0M12 2v4M4.2 9.2l1.4 1.4M19.8 9.2l-1.4 1.4M2 18h0M22 18h0',
    shield: 'M12 3l7 3v5c0 4.5-3 8-7 10-4-2-7-5.5-7-10V6l7-3zM9 12l2 2 4-4',
    gut: 'M8 3a3 3 0 013 3v8a3 3 0 006 0v-1a2 2 0 10-2 2M8 3a3 3 0 00-3 3v9a4 4 0 004 4',
};
</script>

<template>
    <section
        id="program"
        aria-labelledby="program-heading"
        class="relative bg-cream-100 py-20 sm:py-28"
    >
        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="Программа · 3 живых дня"
                    title="Три дня — три понятных шага к энергии"
                    subtitle="Каждый день — это живой эфир с экспертом, разбор темы простым языком и конкретные действия, которые можно применить сразу."
                />
                <h2 id="program-heading" class="sr-only">Программа интенсива</h2>
            </Reveal>

            <ol role="list" class="relative mt-16 space-y-6 lg:space-y-10">
                <!-- vertical timeline line -->
                <span
                    aria-hidden="true"
                    class="absolute left-6 top-4 bottom-4 hidden w-px bg-gradient-to-b from-sage-200 via-sage-300 to-transparent lg:block"
                ></span>

                <Reveal
                    v-for="(day, i) in days"
                    :key="day.label"
                    as="li"
                    :delay="i * 120"
                    class="relative lg:pl-20"
                >
                    <!-- timeline node -->
                    <span
                        aria-hidden="true"
                        class="absolute left-0 top-8 hidden h-12 w-12 items-center justify-center rounded-full border border-sage-200 bg-white text-sage-600 shadow-sm lg:flex"
                    >
                        <svg
                            class="h-6 w-6"
                            viewBox="0 0 24 24"
                            fill="none"
                            stroke="currentColor"
                            stroke-width="1.7"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                        >
                            <path :d="paths[day.icon]" />
                        </svg>
                    </span>

                    <article
                        class="overflow-hidden rounded-3xl border border-sage-100 bg-white/80 shadow-sm shadow-sage-900/5 backdrop-blur-sm transition-all duration-300 hover:shadow-lg hover:shadow-sage-900/10"
                    >
                        <div class="grid gap-6 p-7 sm:p-9 lg:grid-cols-12 lg:gap-10">
                            <div class="lg:col-span-5">
                                <span
                                    class="inline-flex items-center gap-2 rounded-full bg-sage-600 px-3 py-1 text-xs font-semibold uppercase tracking-wide text-white"
                                >
                                    {{ day.label }}
                                </span>
                                <h3
                                    class="mt-4 font-display text-2xl font-semibold leading-snug text-sage-900"
                                >
                                    {{ day.title }}
                                </h3>
                                <p
                                    class="mt-3 text-base leading-relaxed text-sage-700/80"
                                >
                                    {{ day.summary }}
                                </p>
                            </div>

                            <div
                                class="lg:col-span-7 lg:border-l lg:border-sage-100 lg:pl-10"
                            >
                                <p
                                    class="text-xs font-semibold uppercase tracking-wide text-sage-500"
                                >
                                    Что разберём
                                </p>
                                <ul role="list" class="mt-4 grid gap-3">
                                    <li
                                        v-for="topic in day.topics"
                                        :key="topic"
                                        class="flex items-start gap-3"
                                    >
                                        <span
                                            class="mt-0.5 flex h-5 w-5 flex-none items-center justify-center rounded-full bg-sage-100 text-sage-600"
                                            aria-hidden="true"
                                        >
                                            <svg
                                                class="h-3.5 w-3.5"
                                                viewBox="0 0 20 20"
                                                fill="none"
                                                stroke="currentColor"
                                                stroke-width="2.6"
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                            >
                                                <path d="M4 10.5l3.5 3.5L16 5.5" />
                                            </svg>
                                        </span>
                                        <span
                                            class="text-base leading-relaxed text-sage-800"
                                            >{{ topic }}</span
                                        >
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </article>
                </Reveal>
            </ol>
        </div>
    </section>
</template>
