<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const problems = [
    {
        title: 'Просыпаетесь уже уставшими',
        text: 'Будильник прозвенел, а сил как будто и не было. Утро даётся тяжело, хотя спали достаточно.',
        icon: 'bed',
    },
    {
        title: 'Тяжесть после еды',
        text: 'После обычного приёма пищи хочется прилечь, а не продолжать день. Еда будто отнимает энергию.',
        icon: 'plate',
    },
    {
        title: 'Вздутие и дискомфорт',
        text: 'Живот реагирует почти на всё. К вечеру — ощущение наполненности и тяжести.',
        icon: 'wave',
    },
    {
        title: 'Энергия скачет в течение дня',
        text: 'Бодрость сменяется упадком сил, тянет на сладкое и кофе, чтобы продержаться.',
        icon: 'pulse',
    },
    {
        title: 'Пищеварение работает не так, как хотелось бы',
        text: 'Нерегулярность, дискомфорт и ощущение, что ЖКТ живёт своей жизнью.',
        icon: 'leaf',
    },
    {
        title: '«Питаюсь правильно», но лучше не становится',
        text: 'Вы стараетесь следить за едой, но самочувствие всё равно оставляет желать лучшего.',
        icon: 'question',
    },
];

const paths = {
    bed: 'M3 18v-6a2 2 0 012-2h9a4 4 0 014 4v4M3 14h18M3 18v2M21 18v2',
    plate: 'M12 3a9 9 0 100 18 9 9 0 000-18zM12 7v0M9 12h6',
    wave: 'M3 9c2.5-2 4.5-2 7 0s4.5 2 7 0M3 15c2.5-2 4.5-2 7 0s4.5 2 7 0',
    pulse: 'M3 12h4l2 6 4-14 2 8h6',
    leaf: 'M11 20A7 7 0 019.8 6.1C15.5 5 17 4.5 19 2c1 3.5 1.5 9-1.5 12.5A7 7 0 0111 20zM2 22c4-3 6-6 9-12',
    question: 'M9.1 9a3 3 0 015.8 1c0 2-3 3-3 3M12 17h0M12 21a9 9 0 100-18 9 9 0 000 18z',
};
</script>

<template>
    <section
        id="problems"
        aria-labelledby="problems-heading"
        class="relative bg-cream-50 py-20 sm:py-28"
    >
        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="Знакомо?"
                    title="Если хотя бы что-то из этого про вас — вы не одни"
                    subtitle="Большинство людей привыкают жить с этими ощущениями и считают их нормой. На самом деле это сигналы, с которыми можно мягко разобраться."
                />
                <h2 id="problems-heading" class="sr-only">Частые симптомы</h2>
            </Reveal>

            <ul
                role="list"
                class="mt-14 grid gap-5 sm:grid-cols-2 lg:grid-cols-3"
            >
                <Reveal
                    v-for="(problem, i) in problems"
                    :key="problem.title"
                    as="li"
                    :delay="i * 80"
                >
                    <article
                        class="group h-full rounded-3xl border border-sage-100 bg-white/70 p-7 shadow-sm shadow-sage-900/5 backdrop-blur-sm transition-all duration-300 hover:-translate-y-1 hover:border-sage-200 hover:shadow-lg hover:shadow-sage-900/10 motion-reduce:hover:translate-y-0"
                    >
                        <span
                            class="flex h-12 w-12 items-center justify-center rounded-2xl bg-sage-100 text-sage-600 ring-1 ring-sage-200/60"
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
                                <path :d="paths[problem.icon]" />
                            </svg>
                        </span>
                        <h3
                            class="mt-5 text-lg font-semibold text-sage-900"
                        >
                            {{ problem.title }}
                        </h3>
                        <p class="mt-2 text-base leading-relaxed text-sage-700/80">
                            {{ problem.text }}
                        </p>
                    </article>
                </Reveal>
            </ul>

            <Reveal :delay="120">
                <p
                    class="mx-auto mt-12 max-w-2xl text-center text-base text-sage-600"
                >
                    Это не про силу воли и не про жёсткие диеты. Чаще всего дело в
                    привычках, о которых мало кто рассказывает понятным языком.
                </p>
            </Reveal>
        </div>
    </section>
</template>
