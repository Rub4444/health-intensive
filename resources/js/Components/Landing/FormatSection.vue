<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const formats = [
    {
        title: 'Живые эфиры',
        text: 'Три встречи в прямом эфире, где тема разбирается понятно и по шагам.',
        icon: 'video',
    },
    {
        title: 'Вопросы эксперту',
        text: 'Можно задать свой вопрос и получить ответ — без общих фраз.',
        icon: 'chat',
    },
    {
        title: 'Утренние практики',
        text: 'Короткие практики, которые легко повторить дома в своём темпе.',
        icon: 'sunrise',
    },
    {
        title: 'Рецепты завтраков',
        text: 'Простые рецепты из доступных продуктов, которые есть в любом магазине.',
        icon: 'bowl',
    },
    {
        title: 'Простые действия',
        text: 'Никаких сложных схем и таблиц — только понятные шаги на каждый день.',
        icon: 'check',
    },
    {
        title: 'Без экзотики',
        text: 'Не нужно искать редкие добавки или непонятные суперфуды.',
        icon: 'leaf',
    },
];

const paths = {
    video: 'M3 7a2 2 0 012-2h9a2 2 0 012 2v10a2 2 0 01-2 2H5a2 2 0 01-2-2V7zM16 9l5-3v12l-5-3',
    chat: 'M4 5h16a1 1 0 011 1v9a1 1 0 01-1 1H9l-4 4v-4H4a1 1 0 01-1-1V6a1 1 0 011-1zM8 10h0M12 10h0M16 10h0',
    sunrise:
        'M3 18h18M5 18a7 7 0 0114 0M12 2v4M4.2 9.2l1.4 1.4M19.8 9.2l-1.4 1.4',
    bowl: 'M3 11h18a8 8 0 01-16 0M7 11V8a2 2 0 012-2M12 11V7a2 2 0 012-2M5 20h14',
    check: 'M5 12l4 4 10-10',
    leaf: 'M11 20A7 7 0 019.8 6.1C15.5 5 17 4.5 19 2c1 3.5 1.5 9-1.5 12.5A7 7 0 0111 20zM2 22c4-3 6-6 9-12',
};
</script>

<template>
    <section
        id="format"
        aria-labelledby="format-heading"
        class="relative bg-cream-50 py-20 sm:py-28"
    >
        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="Формат"
                    title="Удобно, понятно и без перегруза"
                    subtitle="Интенсив построен так, чтобы его легко было совмещать с обычной жизнью, работой и семьёй."
                />
                <h2 id="format-heading" class="sr-only">Формат интенсива</h2>
            </Reveal>

            <ul role="list" class="mt-14 grid gap-5 sm:grid-cols-2 lg:grid-cols-3">
                <Reveal
                    v-for="(format, i) in formats"
                    :key="format.title"
                    as="li"
                    :delay="i * 80"
                >
                    <article
                        class="flex h-full items-start gap-4 rounded-3xl border border-sage-100 bg-white/70 p-6 shadow-sm shadow-sage-900/5 backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:shadow-lg hover:shadow-sage-900/10 motion-reduce:hover:translate-y-0"
                    >
                        <span
                            class="flex h-12 w-12 flex-none items-center justify-center rounded-2xl bg-sage-100 text-sage-600 ring-1 ring-sage-200/60"
                            aria-hidden="true"
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
                                <path :d="paths[format.icon]" />
                            </svg>
                        </span>
                        <div>
                            <h3 class="text-lg font-semibold text-sage-900">
                                {{ format.title }}
                            </h3>
                            <p
                                class="mt-1.5 text-base leading-relaxed text-sage-700/80"
                            >
                                {{ format.text }}
                            </p>
                        </div>
                    </article>
                </Reveal>
            </ul>
        </div>
    </section>
</template>
