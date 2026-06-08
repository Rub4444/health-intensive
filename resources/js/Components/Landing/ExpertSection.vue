<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';

/** Everything is editable via props so the expert block stays reusable. */
defineProps({
    photo: { type: String, default: '/images/expert-portrait.png' },
    secondaryPhoto: { type: String, default: '/images/expert-clinic.png' },
    name: { type: String, default: '[ИМЯ ЭКСПЕРТА]' },
    role: { type: String, default: '[Специализация · например: нутрициолог, врач]' },
    description: {
        type: String,
        default:
            '[ОПИСАНИЕ ЭКСПЕРТА: коротко об образовании, подходе и опыте. Расскажите, почему эксперту можно доверять, какой у него опыт работы и в чём заключается его подход к здоровью и питанию.]',
    },
    credentials: {
        type: Array,
        default: () => [
            '[образование / квалификация]',
            '[опыт работы, лет]',
            '[кол-во клиентов / учеников]',
            '[ключевая специализация]',
        ],
    },
});
</script>

<template>
    <section
        id="expert"
        aria-labelledby="expert-heading"
        class="relative overflow-hidden bg-white py-20 sm:py-28"
    >
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10"
            style="
                background:
                    radial-gradient(45% 50% at 12% 18%, rgba(195, 221, 201, 0.35), transparent 65%),
                    radial-gradient(45% 50% at 95% 85%, rgba(240, 232, 217, 0.5), transparent 70%);
            "
        ></div>

        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <div class="grid items-center gap-14 lg:grid-cols-12 lg:gap-16">
                <!-- Portrait composition -->
                <Reveal class="lg:col-span-5">
                    <div class="relative mx-auto max-w-sm">
                        <div
                            aria-hidden="true"
                            class="absolute -inset-4 -z-10 rounded-[2.75rem] bg-sage-100/70 blur-2xl"
                        ></div>

                        <figure
                            class="relative overflow-hidden rounded-[2.5rem] bg-sage-100 shadow-2xl shadow-sage-900/15 ring-1 ring-white/60"
                        >
                            <img
                                :src="photo"
                                :alt="`Фотография эксперта интенсива: ${name}`"
                                class="aspect-[4/5] h-full w-full object-cover"
                                loading="lazy"
                                decoding="async"
                            />
                        </figure>

                        <!-- Floating secondary photo -->
                        <figure
                            class="absolute -bottom-8 -right-4 hidden w-36 overflow-hidden rounded-3xl border-4 border-white bg-sage-100 shadow-xl shadow-sage-900/20 sm:block"
                        >
                            <img
                                :src="secondaryPhoto"
                                alt=""
                                aria-hidden="true"
                                class="aspect-square h-full w-full object-cover"
                                loading="lazy"
                                decoding="async"
                            />
                        </figure>

                        <!-- Floating trust chip -->
                        <div
                            class="absolute -left-3 top-8 flex items-center gap-2 rounded-2xl border border-sage-100 bg-white/85 px-4 py-2.5 shadow-lg backdrop-blur-md"
                        >
                            <span
                                class="flex h-9 w-9 items-center justify-center rounded-xl bg-sage-600/10 text-sage-700"
                                aria-hidden="true"
                            >
                                <svg
                                    class="h-5 w-5"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="1.8"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                >
                                    <path d="M12 3l7 3v5c0 4.5-3 8-7 10-4-2-7-5.5-7-10V6l7-3zM9 12l2 2 4-4" />
                                </svg>
                            </span>
                            <span class="text-sm font-semibold text-sage-900"
                                >Доказательный подход</span
                            >
                        </div>
                    </div>
                </Reveal>

                <!-- Bio -->
                <Reveal class="lg:col-span-7" :delay="120">
                    <p
                        class="inline-flex items-center gap-2 text-sm font-semibold uppercase tracking-[0.14em] text-sage-600"
                    >
                        <span class="h-px w-6 bg-sage-300" aria-hidden="true"></span>
                        Ваш эксперт
                    </p>
                    <h2
                        id="expert-heading"
                        class="mt-4 font-display text-3xl font-semibold leading-tight tracking-tight text-sage-900 sm:text-4xl"
                    >
                        {{ name }}
                    </h2>
                    <p class="mt-2 text-lg font-medium text-sage-600">
                        {{ role }}
                    </p>
                    <p class="mt-6 max-w-xl text-lg leading-relaxed text-sage-700/85">
                        {{ description }}
                    </p>

                    <dl class="mt-8 grid gap-4 sm:grid-cols-2">
                        <div
                            v-for="credential in credentials"
                            :key="credential"
                            class="flex items-start gap-3 rounded-2xl border border-sage-100 bg-cream-50/70 px-4 py-3"
                        >
                            <span
                                class="mt-0.5 flex h-6 w-6 flex-none items-center justify-center rounded-full bg-sage-100 text-sage-600"
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
                            <dd class="text-base font-medium text-sage-800">
                                {{ credential }}
                            </dd>
                        </div>
                    </dl>
                </Reveal>
            </div>
        </div>
    </section>
</template>
