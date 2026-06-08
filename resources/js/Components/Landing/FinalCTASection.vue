<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';

defineProps({
    headline: {
        type: String,
        default: 'Начните заботиться о своём здоровье уже сейчас',
    },
    subheadline: {
        type: String,
        default:
            'Небольшие изменения в утренних привычках и питании могут заметно повлиять на самочувствие уже в ближайшие дни.',
    },
    ctaLabel: { type: String, default: 'Принять участие' },
    ctaHref: { type: String, default: '#register' },
    startDate: { type: String, default: '[Дата интенсива]' },
});

defineEmits(['cta']);
</script>

<template>
    <section
        id="register"
        aria-labelledby="final-cta-heading"
        class="relative overflow-hidden bg-cream-100 py-20 sm:py-28"
    >
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10"
            style="
                background:
                    radial-gradient(60% 60% at 50% 110%, rgba(110, 166, 125, 0.3), transparent 65%),
                    radial-gradient(45% 45% at 12% 0%, rgba(195, 221, 201, 0.4), transparent 70%);
            "
        ></div>

        <div class="mx-auto w-full max-w-4xl px-5 sm:px-8">
            <Reveal>
                <div
                    class="relative overflow-hidden rounded-[2.75rem] border border-sage-200/70 bg-white/70 px-6 py-14 text-center shadow-2xl shadow-sage-900/10 backdrop-blur-md sm:px-12 sm:py-16"
                >
                    <div
                        aria-hidden="true"
                        class="bg-noise pointer-events-none absolute inset-0 opacity-[0.04]"
                    ></div>

                    <span
                        class="relative inline-flex items-center gap-2 rounded-full border border-sage-200 bg-white/70 px-4 py-1.5 text-sm font-semibold text-sage-700 shadow-sm"
                    >
                        <span class="relative flex h-2 w-2" aria-hidden="true">
                            <span
                                class="absolute inline-flex h-full w-full animate-ping rounded-full bg-sage-400 opacity-75"
                            ></span>
                            <span
                                class="relative inline-flex h-2 w-2 rounded-full bg-sage-500"
                            ></span>
                        </span>
                        Старт: {{ startDate }}
                    </span>

                    <h2
                        id="final-cta-heading"
                        class="relative mx-auto mt-6 max-w-2xl font-display text-3xl font-semibold leading-[1.12] tracking-tight text-sage-900 sm:text-4xl"
                    >
                        {{ headline }}
                    </h2>
                    <p
                        class="relative mx-auto mt-5 max-w-xl text-lg leading-relaxed text-sage-700/85"
                    >
                        {{ subheadline }}
                    </p>

                    <div
                        class="relative mt-9 flex flex-col items-center justify-center gap-4 sm:flex-row"
                    >
                        <a
                            :href="ctaHref"
                            class="group inline-flex w-full items-center justify-center gap-2 rounded-full bg-sage-600 px-9 py-4 text-base font-semibold text-white shadow-lg shadow-sage-600/25 transition-all duration-300 hover:-translate-y-0.5 hover:bg-sage-700 hover:shadow-xl hover:shadow-sage-600/30 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sage-600 motion-reduce:hover:translate-y-0 sm:w-auto"
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
                        <p class="text-sm text-sage-600">
                            Спокойный темп · понятные шаги · поддержка эксперта
                        </p>
                    </div>
                </div>
            </Reveal>
        </div>
    </section>
</template>
