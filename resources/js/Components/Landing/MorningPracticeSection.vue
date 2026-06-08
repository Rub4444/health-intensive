<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const practices = [
    {
        title: 'Утренняя йога',
        text: 'Мягкие движения, чтобы разбудить тело и спокойно войти в день.',
        icon: 'yoga',
    },
    {
        title: 'Упражнения для лимфы',
        text: 'Простые техники, которые помогают телу мягко «проснуться» изнутри.',
        icon: 'flow',
    },
    {
        title: 'Упражнения для кишечника',
        text: 'Бережная активация пищеварения с самого утра — основа лёгкости.',
        icon: 'gut',
    },
    {
        title: 'Поддержка желчеоттока',
        text: 'Несложные практики, которые помогают пищеварению работать ровнее.',
        icon: 'drop',
    },
    {
        title: 'Полезный завтрак',
        text: 'Готовим вместе простой и вкусный завтрак без экзотических продуктов.',
        icon: 'bowl',
    },
    {
        title: 'Новые привычки',
        text: 'Каждое утро добавляем одно небольшое действие, которое легко закрепить.',
        icon: 'seed',
    },
];

const paths = {
    yoga: 'M12 4a1.6 1.6 0 100-3.2A1.6 1.6 0 0012 4zM12 6v6M5 9h14M12 12l-4 8M12 12l4 8',
    flow: 'M3 8c3-3 6-3 9 0s6 3 9 0M3 16c3-3 6-3 9 0s6 3 9 0',
    gut: 'M8 3a3 3 0 013 3v8a3 3 0 006 0v-1a2 2 0 10-2 2M8 3a3 3 0 00-3 3v9a4 4 0 004 4',
    drop: 'M12 3s6 6.5 6 11a6 6 0 01-12 0c0-4.5 6-11 6-11zM9.5 14a2.5 2.5 0 002.5 2.5',
    bowl: 'M3 11h18a8 8 0 01-16 0M7 11V8a2 2 0 012-2M12 11V7a2 2 0 012-2M5 20h14',
    seed: 'M12 22V12M12 12c0-3 2-5 5-5 0 3-2 5-5 5zM12 14c0-3-2-5-5-5 0 3 2 5 5 5z',
};
</script>

<template>
    <section
        id="mornings"
        aria-labelledby="mornings-heading"
        class="relative overflow-hidden bg-sage-700 py-20 text-cream-50 sm:py-28"
    >
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10"
            style="
                background:
                    radial-gradient(55% 55% at 80% 10%, rgba(156, 196, 166, 0.25), transparent 65%),
                    radial-gradient(50% 50% at 10% 90%, rgba(31, 55, 39, 0.6), transparent 70%);
            "
        ></div>
        <div
            aria-hidden="true"
            class="bg-noise pointer-events-none absolute inset-0 -z-10 opacity-[0.06]"
        ></div>

        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <Reveal>
                <div class="max-w-2xl">
                    <p
                        class="inline-flex items-center gap-2 text-sm font-semibold uppercase tracking-[0.14em] text-sage-200"
                    >
                        <span class="h-px w-6 bg-sage-300" aria-hidden="true"></span>
                        Каждое утро на интенсиве
                    </p>
                    <h2
                        id="mornings-heading"
                        class="mt-4 font-display text-3xl font-semibold leading-[1.12] tracking-tight sm:text-4xl"
                    >
                        Утренняя практика, которая занимает минуты, а ощущается весь
                        день
                    </h2>
                    <p class="mt-4 text-lg leading-relaxed text-cream-100/85">
                        Мы вместе проживаем утро так, как стоит. Никакого спорта до
                        изнеможения — только мягкие, выполнимые действия.
                    </p>
                </div>
            </Reveal>

            <ul role="list" class="mt-14 grid gap-5 sm:grid-cols-2 lg:grid-cols-3">
                <Reveal
                    v-for="(practice, i) in practices"
                    :key="practice.title"
                    as="li"
                    :delay="i * 80"
                >
                    <article
                        class="group h-full rounded-3xl border border-white/10 bg-white/10 p-7 backdrop-blur-md transition-all duration-300 hover:-translate-y-1 hover:bg-white/15 motion-reduce:hover:translate-y-0"
                    >
                        <span
                            class="flex h-12 w-12 items-center justify-center rounded-2xl bg-cream-50/15 text-cream-50 ring-1 ring-white/20"
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
                                <path :d="paths[practice.icon]" />
                            </svg>
                        </span>
                        <h3 class="mt-5 text-lg font-semibold text-cream-50">
                            {{ practice.title }}
                        </h3>
                        <p class="mt-2 text-base leading-relaxed text-cream-100/80">
                            {{ practice.text }}
                        </p>
                    </article>
                </Reveal>
            </ul>
        </div>
    </section>
</template>
