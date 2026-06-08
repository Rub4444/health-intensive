<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const results = [
    {
        title: 'Больше энергии',
        text: 'Стабильные силы с утра и до вечера — без «провалов» и постоянной тяги к кофе.',
        icon: 'sun',
    },
    {
        title: 'Лёгкость после еды',
        text: 'Приёмы пищи перестают вызывать тяжесть и сонливость. Еда снова даёт ресурс.',
        icon: 'feather',
    },
    {
        title: 'Стабильное настроение',
        text: 'Меньше раздражительности и тревожных перепадов — ровный эмоциональный фон.',
        icon: 'smile',
    },
    {
        title: 'Понятная система питания',
        text: 'Без жёстких запретов и подсчётов. Простые принципы, которые легко соблюдать.',
        icon: 'list',
    },
    {
        title: 'Здоровые привычки',
        text: 'Небольшие ежедневные ритуалы, которые встраиваются в жизнь и остаются с вами.',
        icon: 'repeat',
    },
    {
        title: 'Улучшение самочувствия',
        text: 'Комфортное пищеварение, спокойный живот и ощущение, что тело вас поддерживает.',
        icon: 'heart',
    },
];

const paths = {
    sun: 'M12 7a5 5 0 100 10 5 5 0 000-10zM12 2v2M12 20v2M4 12H2M22 12h-2M5 5l1.5 1.5M17.5 17.5L19 19M19 5l-1.5 1.5M6.5 17.5L5 19',
    feather: 'M20 4a6 6 0 00-8.5 0L4 11.5V20h8.5L20 12.5A6 6 0 0020 4zM4 20l7-7M14 6l4 4',
    smile: 'M12 21a9 9 0 100-18 9 9 0 000 18zM9 10h0M15 10h0M8.5 14.5a4 4 0 007 0',
    list: 'M8 6h12M8 12h12M8 18h12M4 6h0M4 12h0M4 18h0',
    repeat: 'M4 9a8 8 0 0113-3l3 3M20 15a8 8 0 01-13 3l-3-3M20 4v5h-5M4 20v-5h5',
    heart: 'M12 20s-7-4.5-9.5-9A4.5 4.5 0 0112 5a4.5 4.5 0 019.5 6c-2.5 4.5-9.5 9-9.5 9z',
};
</script>

<template>
    <section
        id="results"
        aria-labelledby="results-heading"
        class="relative overflow-hidden bg-white py-20 sm:py-28"
    >
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10"
            style="
                background:
                    radial-gradient(50% 50% at 85% 0%, rgba(195, 221, 201, 0.35), transparent 70%),
                    radial-gradient(45% 45% at 5% 100%, rgba(240, 232, 217, 0.55), transparent 70%);
            "
        ></div>

        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="К чему вы придёте"
                    title="Что меняется уже за 3 дня"
                    subtitle="Это не обещание «волшебной таблетки». Это конкретные, ощутимые изменения, которые появляются, когда тело получает понятную поддержку."
                />
                <h2 id="results-heading" class="sr-only">Результаты</h2>
            </Reveal>

            <ul
                role="list"
                class="mt-14 grid gap-5 sm:grid-cols-2 lg:grid-cols-3"
            >
                <Reveal
                    v-for="(result, i) in results"
                    :key="result.title"
                    as="li"
                    :delay="i * 80"
                >
                    <article
                        class="relative h-full overflow-hidden rounded-3xl border border-sage-100 bg-gradient-to-b from-sage-50/60 to-white p-7 shadow-sm shadow-sage-900/5 transition-all duration-300 hover:-translate-y-1 hover:shadow-lg hover:shadow-sage-900/10 motion-reduce:hover:translate-y-0"
                    >
                        <span
                            class="flex h-12 w-12 items-center justify-center rounded-2xl bg-sage-600 text-white shadow-sm shadow-sage-600/30"
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
                                <path :d="paths[result.icon]" />
                            </svg>
                        </span>
                        <h3 class="mt-5 text-lg font-semibold text-sage-900">
                            {{ result.title }}
                        </h3>
                        <p class="mt-2 text-base leading-relaxed text-sage-700/80">
                            {{ result.text }}
                        </p>
                    </article>
                </Reveal>
            </ul>
        </div>
    </section>
</template>
