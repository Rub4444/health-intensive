<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

defineProps({
    price: { type: String, default: '990 ₽' },
    startDate: { type: String, default: '[дата интенсива]' },
    ctaLabel: { type: String, default: 'Принять участие' },
    ctaHref: { type: String, default: '#register' },
});

defineEmits(['cta']);

const included = [
    'Всё обучение — 3 живых дня',
    'Живые эфиры с экспертом',
    'Утренние практики на каждый день',
    'Рецепты полезных завтраков',
    'Доступ к материалам и записям',
    'Ответы на ваши вопросы',
];
</script>

<template>
    <section
        id="pricing"
        aria-labelledby="pricing-heading"
        class="relative overflow-hidden bg-white py-20 sm:py-28"
    >
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10"
            style="
                background:
                    radial-gradient(50% 50% at 50% 0%, rgba(195, 221, 201, 0.4), transparent 70%),
                    linear-gradient(180deg, #ffffff 0%, #fdfbf7 100%);
            "
        ></div>

        <div class="mx-auto w-full max-w-4xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="Участие"
                    title="Один доступный шаг к лучшему самочувствию"
                    subtitle="Полноценный 3-дневный интенсив по цене чашки кофе на двоих. Без скрытых платежей и допродаж."
                />
                <h2 id="pricing-heading" class="sr-only">Стоимость участия</h2>
            </Reveal>

            <Reveal :delay="120">
                <div
                    class="relative mt-12 overflow-hidden rounded-[2.5rem] border border-sage-100 bg-white shadow-2xl shadow-sage-900/10"
                >
                    <div class="grid lg:grid-cols-12">
                        <!-- Included -->
                        <div class="p-8 sm:p-10 lg:col-span-7">
                            <h3
                                class="font-display text-2xl font-semibold text-sage-900"
                            >
                                3-дневный онлайн-интенсив
                            </h3>
                            <p class="mt-2 text-base text-sage-700/80">
                                Всё, что нужно, чтобы мягко перезапустить утро,
                                питание и энергию.
                            </p>
                            <ul role="list" class="mt-7 grid gap-3 sm:grid-cols-2">
                                <li
                                    v-for="item in included"
                                    :key="item"
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
                                        class="text-base leading-snug text-sage-800"
                                        >{{ item }}</span
                                    >
                                </li>
                            </ul>
                        </div>

                        <!-- Price panel -->
                        <div
                            class="relative flex flex-col justify-center gap-6 bg-sage-700 p-8 text-cream-50 sm:p-10 lg:col-span-5"
                        >
                            <div
                                aria-hidden="true"
                                class="bg-noise pointer-events-none absolute inset-0 opacity-[0.06]"
                            ></div>
                            <div class="relative">
                                <p
                                    class="text-sm font-medium uppercase tracking-wide text-sage-200"
                                >
                                    Стоимость участия
                                </p>
                                <p class="mt-1 flex items-baseline gap-2">
                                    <span
                                        class="font-display text-5xl font-semibold"
                                        >{{ price }}</span
                                    >
                                </p>
                                <p class="mt-2 text-sm text-cream-100/80">
                                    Единоразовый платёж · доступ остаётся с вами
                                </p>
                            </div>

                            <a
                                :href="ctaHref"
                                class="group relative inline-flex items-center justify-center gap-2 rounded-full bg-cream-50 px-8 py-4 text-base font-semibold text-sage-800 shadow-lg transition-all duration-300 hover:-translate-y-0.5 hover:bg-white hover:shadow-xl focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-cream-50 motion-reduce:hover:translate-y-0"
                                @click="$emit('cta')"
                            >
                                {{ ctaLabel }}
                                <svg
                                    class="h-5 w-5 transition-transform duration-300 group-hover:translate-x-1 motion-reduce:transition-none"
                                    viewBox="0 0 20 20"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="2.2"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    aria-hidden="true"
                                >
                                    <path d="M4 10h12M11 5l5 5-5 5" />
                                </svg>
                            </a>

                            <p
                                class="relative flex items-center gap-2 text-sm text-cream-100/85"
                            >
                                <svg
                                    class="h-4 w-4 flex-none"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="1.8"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    aria-hidden="true"
                                >
                                    <path d="M8 7V5a4 4 0 118 0v2M5 10h14v9a2 2 0 01-2 2H7a2 2 0 01-2-2v-9z" />
                                </svg>
                                Старт: {{ startDate }}
                            </p>
                        </div>
                    </div>
                </div>
            </Reveal>
        </div>
    </section>
</template>
