<script setup>
import { computed, onBeforeUnmount, onMounted, ref } from 'vue';

/**
 * Premium, conversion-focused hero for a 3-day health intensive.
 * Fully reusable: all marketing copy is overridable via props.
 */
const props = defineProps({
    badge: {
        type: String,
        default: '3-дневный онлайн-интенсив',
    },
    headline: {
        type: String,
        default: 'Начните утро так, чтобы энергии хватало на весь день',
    },
    subheadline: {
        type: String,
        default:
            'За 3 дня разберётесь, как утренние привычки, питание и здоровье ЖКТ влияют на самочувствие, пищеварение и уровень энергии.',
    },
    benefits: {
        type: Array,
        default: () => [
            'больше энергии',
            'лёгкость после еды',
            'стабильное настроение',
            'понятная система питания',
        ],
    },
    ctaLabel: {
        type: String,
        default: 'Принять участие',
    },
    ctaHref: {
        type: String,
        default: '#register',
    },
    startDate: {
        type: String,
        default: '[дата интенсива]',
    },
    price: {
        type: String,
        default: '990 ₽',
    },
    participants: {
        type: String,
        default: 'Более 1000 участников уже улучшили своё самочувствие',
    },
    rating: {
        type: Number,
        default: 4.9,
    },
});

defineEmits(['cta']);

/* ----- Entrance reveal (staggered fade-up) ----- */
const mounted = ref(false);

/* ----- Pointer parallax (disabled for reduced-motion users) ----- */
const allowMotion = ref(true);
const parallax = ref({ x: 0, y: 0 });

const visualStyle = computed(() => ({
    transform: `translate3d(${parallax.value.x * 14}px, ${parallax.value.y * 14}px, 0)`,
}));
const blobStyle = computed(() => ({
    transform: `translate3d(${parallax.value.x * -26}px, ${parallax.value.y * -26}px, 0)`,
}));

let frame = 0;
function handlePointer(event) {
    if (!allowMotion.value) return;
    cancelAnimationFrame(frame);
    frame = requestAnimationFrame(() => {
        const x = (event.clientX / window.innerWidth - 0.5) * 2;
        const y = (event.clientY / window.innerHeight - 0.5) * 2;
        parallax.value = { x, y };
    });
}

const floatingCards = [
    {
        title: 'Утренняя энергия',
        caption: 'ритуалы пробуждения',
        position: 'left-1 top-10 sm:-left-6 sm:top-14',
        animation: 'animate-float',
        delay: 'delay-300',
        icon: 'sun',
    },
    {
        title: 'Здоровое пищеварение',
        caption: 'лёгкость каждый день',
        position: 'right-0 top-1/2 sm:-right-8',
        animation: 'animate-float-delayed',
        delay: 'delay-500',
        icon: 'leaf',
    },
    {
        title: 'Полезные привычки',
        caption: 'система, а не диета',
        position: 'bottom-6 left-6 sm:-left-4 sm:bottom-10',
        animation: 'animate-float-slow',
        delay: 'delay-700',
        icon: 'spark',
    },
];

const avatars = [
    { src: 'https://i.pravatar.cc/96?img=32', alt: 'Участница интенсива' },
    { src: 'https://i.pravatar.cc/96?img=12', alt: 'Участник интенсива' },
    { src: 'https://i.pravatar.cc/96?img=45', alt: 'Участница интенсива' },
];

onMounted(() => {
    const media = window.matchMedia('(prefers-reduced-motion: reduce)');
    allowMotion.value = !media.matches;
    requestAnimationFrame(() => (mounted.value = true));
    if (allowMotion.value) {
        window.addEventListener('pointermove', handlePointer, { passive: true });
    }
});

onBeforeUnmount(() => {
    window.removeEventListener('pointermove', handlePointer);
    cancelAnimationFrame(frame);
});
</script>

<template>
    <section
        aria-labelledby="hero-heading"
        class="relative isolate overflow-hidden bg-cream-50 font-sans text-sage-900"
    >
        <!-- Ambient background: radial gradients, green glow, beige tones -->
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10"
            style="
                background:
                    radial-gradient(60% 55% at 78% 18%, rgba(110, 166, 125, 0.28), transparent 60%),
                    radial-gradient(45% 45% at 12% 12%, rgba(240, 232, 217, 0.9), transparent 70%),
                    radial-gradient(55% 60% at 88% 90%, rgba(195, 221, 201, 0.45), transparent 65%),
                    linear-gradient(180deg, #fdfbf7 0%, #f8f3ea 100%);
            "
        ></div>

        <!-- Decorative organic blobs (parallax) -->
        <div
            aria-hidden="true"
            class="pointer-events-none absolute inset-0 -z-10 transition-transform duration-300 ease-out"
            :style="allowMotion ? blobStyle : undefined"
        >
            <div
                class="animate-blob absolute -left-24 top-[-10%] h-80 w-80 rounded-full bg-sage-200/50 blur-3xl"
            ></div>
            <div
                class="animate-blob-slow absolute right-[-8%] top-1/3 h-96 w-96 rounded-full bg-sage-300/30 blur-3xl"
            ></div>
            <div
                class="animate-blob absolute bottom-[-12%] left-1/3 h-72 w-72 rounded-full bg-cream-300/60 blur-3xl"
            ></div>
        </div>

        <!-- Soft noise texture -->
        <div
            aria-hidden="true"
            class="bg-noise pointer-events-none absolute inset-0 -z-10 opacity-[0.04] mix-blend-multiply"
        ></div>

        <div class="mx-auto w-full max-w-7xl px-5 py-16 sm:px-8 sm:py-20 lg:py-28">
            <div class="grid items-center gap-14 lg:grid-cols-12 lg:gap-10">
                <!-- ============ LEFT: CONTENT ============ -->
                <div class="lg:col-span-6 xl:col-span-5">
                    <!-- Premium badge -->
                    <div
                        class="inline-flex items-center gap-2 rounded-full border border-sage-200 bg-white/70 px-4 py-1.5 text-sm font-semibold text-sage-700 shadow-sm backdrop-blur transition-all duration-700 ease-out"
                        :class="
                            mounted
                                ? 'translate-y-0 opacity-100'
                                : 'translate-y-4 opacity-0'
                        "
                    >
                        <span
                            class="relative flex h-2 w-2"
                            aria-hidden="true"
                        >
                            <span
                                class="absolute inline-flex h-full w-full animate-ping rounded-full bg-sage-400 opacity-75"
                            ></span>
                            <span
                                class="relative inline-flex h-2 w-2 rounded-full bg-sage-500"
                            ></span>
                        </span>
                        {{ badge }}
                    </div>

                    <!-- Headline -->
                    <h1
                        id="hero-heading"
                        class="mt-6 font-display text-4xl font-semibold leading-[1.08] tracking-tight text-sage-900 transition-all duration-700 ease-out sm:text-5xl xl:text-6xl"
                        :class="
                            mounted
                                ? 'translate-y-0 opacity-100 delay-100'
                                : 'translate-y-5 opacity-0'
                        "
                    >
                        Начните утро так, чтобы энергии хватало на
                        <span class="relative whitespace-nowrap text-sage-600">
                            весь день
                            <svg
                                class="absolute -bottom-2 left-0 h-3 w-full text-sage-300"
                                viewBox="0 0 200 12"
                                fill="none"
                                preserveAspectRatio="none"
                                aria-hidden="true"
                            >
                                <path
                                    d="M2 9C40 4 120 2 198 6"
                                    stroke="currentColor"
                                    stroke-width="3"
                                    stroke-linecap="round"
                                />
                            </svg>
                        </span>
                    </h1>

                    <!-- Subheadline -->
                    <p
                        class="mt-6 max-w-xl text-lg leading-relaxed text-sage-700/80 transition-all duration-700 ease-out"
                        :class="
                            mounted
                                ? 'translate-y-0 opacity-100 delay-200'
                                : 'translate-y-5 opacity-0'
                        "
                    >
                        {{ subheadline }}
                    </p>

                    <!-- Benefits -->
                    <ul
                        class="mt-8 grid gap-3 sm:grid-cols-2"
                        role="list"
                    >
                        <li
                            v-for="(benefit, i) in benefits"
                            :key="benefit"
                            class="flex items-center gap-3 transition-all duration-700 ease-out"
                            :class="
                                mounted
                                    ? 'translate-y-0 opacity-100'
                                    : 'translate-y-4 opacity-0'
                            "
                            :style="{
                                transitionDelay: mounted
                                    ? `${300 + i * 90}ms`
                                    : '0ms',
                            }"
                        >
                            <span
                                class="flex h-7 w-7 flex-none items-center justify-center rounded-full bg-sage-100 text-sage-600 ring-1 ring-sage-200"
                                aria-hidden="true"
                            >
                                <svg
                                    class="h-4 w-4"
                                    viewBox="0 0 20 20"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="2.4"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                >
                                    <path d="M4 10.5l3.5 3.5L16 5.5" />
                                </svg>
                            </span>
                            <span class="text-base font-medium text-sage-800">{{
                                benefit
                            }}</span>
                        </li>
                    </ul>

                    <!-- CTA + secondary info -->
                    <div
                        class="mt-10 flex flex-col gap-6 transition-all duration-700 delay-700 ease-out sm:flex-row sm:items-center"
                        :class="
                            mounted
                                ? 'translate-y-0 opacity-100'
                                : 'translate-y-4 opacity-0'
                        "
                    >
                        <a
                            :href="ctaHref"
                            class="group inline-flex items-center justify-center gap-2 rounded-full bg-sage-600 px-8 py-4 text-base font-semibold text-white shadow-lg shadow-sage-600/25 transition-all duration-300 ease-out hover:-translate-y-0.5 hover:bg-sage-700 hover:shadow-xl hover:shadow-sage-600/30 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-sage-600 active:translate-y-0 motion-reduce:transition-none motion-reduce:hover:translate-y-0"
                            @click="$emit('cta')"
                        >
                            {{ ctaLabel }}
                            <svg
                                class="h-5 w-5 transition-transform duration-300 ease-out group-hover:translate-x-1 motion-reduce:transition-none"
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

                        <dl class="flex items-center gap-6">
                            <div class="flex flex-col">
                                <dt
                                    class="text-xs font-medium uppercase tracking-wide text-sage-500"
                                >
                                    Старт
                                </dt>
                                <dd class="text-base font-semibold text-sage-800">
                                    {{ startDate }}
                                </dd>
                            </div>
                            <div
                                class="h-9 w-px bg-sage-200"
                                aria-hidden="true"
                            ></div>
                            <div class="flex flex-col">
                                <dt
                                    class="text-xs font-medium uppercase tracking-wide text-sage-500"
                                >
                                    Цена
                                </dt>
                                <dd class="text-base font-semibold text-sage-800">
                                    {{ price }}
                                </dd>
                            </div>
                        </dl>
                    </div>
                </div>

                <!-- ============ RIGHT: VISUAL COMPOSITION ============ -->
                <div class="lg:col-span-6 xl:col-span-7">
                    <div
                        class="relative mx-auto max-w-md transition-all duration-1000 ease-out lg:max-w-xl"
                        :class="
                            mounted
                                ? 'translate-y-0 opacity-100'
                                : 'translate-y-8 opacity-0'
                        "
                    >
                        <!-- Glow behind the card -->
                        <div
                            aria-hidden="true"
                            class="absolute inset-6 -z-10 rounded-[2.5rem] bg-sage-300/40 blur-2xl"
                        ></div>

                        <!-- Rounded image card (parallax) -->
                        <div
                            class="relative aspect-[4/5] overflow-hidden rounded-[2.25rem] bg-sage-100 shadow-2xl shadow-sage-900/15 ring-1 ring-white/60 transition-transform duration-300 ease-out sm:aspect-square"
                            :style="allowMotion ? visualStyle : undefined"
                        >
                            <img
                                src="https://images.unsplash.com/photo-1490645935967-10de6ba17061?auto=format&fit=crop&w=1100&q=80"
                                alt="Здоровый завтрак: свежие овощи, зелень и сбалансированная еда для утренней энергии"
                                class="h-full w-full object-cover"
                                loading="eager"
                                decoding="async"
                            />
                            <!-- Warm tint for brand cohesion -->
                            <div
                                aria-hidden="true"
                                class="absolute inset-0 bg-gradient-to-tr from-sage-900/35 via-transparent to-cream-100/20"
                            ></div>

                            <!-- In-card stat chip -->
                            <div
                                class="absolute bottom-4 left-4 right-4 flex items-center gap-3 rounded-2xl border border-white/40 bg-white/75 px-4 py-3 shadow-lg backdrop-blur-md"
                            >
                                <span
                                    class="flex h-10 w-10 flex-none items-center justify-center rounded-xl bg-sage-600/10 text-sage-700"
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
                                        <path d="M3 12h4l2 6 4-14 2 8h6" />
                                    </svg>
                                </span>
                                <div>
                                    <p
                                        class="text-sm font-semibold leading-tight text-sage-900"
                                    >
                                        Стабильная энергия
                                    </p>
                                    <p class="text-xs text-sage-600">
                                        без спадов в течение дня
                                    </p>
                                </div>
                            </div>
                        </div>

                        <!-- Floating glassmorphism cards -->
                        <div
                            v-for="(card, i) in floatingCards"
                            :key="card.title"
                            class="absolute z-10 transition-all duration-1000 ease-out"
                            :class="[
                                card.position,
                                card.delay,
                                mounted
                                    ? 'translate-y-0 opacity-100'
                                    : 'translate-y-6 opacity-0',
                            ]"
                        >
                            <div
                                :class="allowMotion ? card.animation : ''"
                                class="flex items-center gap-3 rounded-2xl border border-white/50 bg-white/65 px-4 py-3 shadow-xl shadow-sage-900/10 backdrop-blur-md"
                            >
                                <span
                                    class="flex h-9 w-9 flex-none items-center justify-center rounded-xl bg-sage-100 text-sage-600"
                                    aria-hidden="true"
                                >
                                    <!-- sun -->
                                    <svg
                                        v-if="card.icon === 'sun'"
                                        class="h-5 w-5"
                                        viewBox="0 0 24 24"
                                        fill="none"
                                        stroke="currentColor"
                                        stroke-width="1.8"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                    >
                                        <circle cx="12" cy="12" r="4" />
                                        <path
                                            d="M12 2v2M12 20v2M4 12H2M22 12h-2M5 5l1.5 1.5M17.5 17.5L19 19M19 5l-1.5 1.5M6.5 17.5L5 19"
                                        />
                                    </svg>
                                    <!-- leaf -->
                                    <svg
                                        v-else-if="card.icon === 'leaf'"
                                        class="h-5 w-5"
                                        viewBox="0 0 24 24"
                                        fill="none"
                                        stroke="currentColor"
                                        stroke-width="1.8"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                    >
                                        <path
                                            d="M11 20A7 7 0 019.8 6.1C15.5 5 17 4.5 19 2c1 3.5 1.5 9-1.5 12.5A7 7 0 0111 20z"
                                        />
                                        <path d="M2 22c4-3 6-6 9-12" />
                                    </svg>
                                    <!-- spark -->
                                    <svg
                                        v-else
                                        class="h-5 w-5"
                                        viewBox="0 0 24 24"
                                        fill="none"
                                        stroke="currentColor"
                                        stroke-width="1.8"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                    >
                                        <path
                                            d="M12 3l1.8 4.6L18 9.4l-4.2 1.8L12 16l-1.8-4.8L6 9.4l4.2-1.8z"
                                        />
                                        <path d="M19 14l.9 2.3L22 17l-2.1.9L19 20l-.9-2.1L16 17l2.1-.7z" />
                                    </svg>
                                </span>
                                <div class="pr-1">
                                    <p
                                        class="text-sm font-semibold leading-tight text-sage-900"
                                    >
                                        {{ card.title }}
                                    </p>
                                    <p class="text-xs text-sage-600">
                                        {{ card.caption }}
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- ============ SOCIAL PROOF STRIP ============ -->
            <div
                class="mt-16 flex flex-col items-center gap-5 rounded-3xl border border-sage-100 bg-white/60 px-6 py-5 shadow-sm backdrop-blur-sm transition-all duration-700 ease-out sm:flex-row sm:justify-between sm:gap-8 lg:mt-20"
                :class="
                    mounted ? 'translate-y-0 opacity-100' : 'translate-y-4 opacity-0'
                "
                style="transition-delay: 900ms"
            >
                <div class="flex items-center gap-4">
                    <ul class="flex -space-x-3" role="list" aria-hidden="true">
                        <li v-for="avatar in avatars" :key="avatar.src">
                            <img
                                :src="avatar.src"
                                :alt="avatar.alt"
                                class="h-11 w-11 rounded-full border-2 border-white object-cover shadow-sm"
                                loading="lazy"
                                decoding="async"
                            />
                        </li>
                        <li
                            class="flex h-11 w-11 items-center justify-center rounded-full border-2 border-white bg-sage-600 text-xs font-semibold text-white shadow-sm"
                        >
                            1K+
                        </li>
                    </ul>
                    <p class="max-w-xs text-sm font-medium text-sage-700">
                        {{ participants }}
                    </p>
                </div>

                <div
                    class="flex items-center gap-3 border-sage-100 sm:border-l sm:pl-8"
                >
                    <div class="flex items-center gap-0.5" aria-hidden="true">
                        <svg
                            v-for="star in 5"
                            :key="star"
                            class="h-5 w-5 text-amber-400"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                        >
                            <path
                                d="M10 1.5l2.6 5.3 5.9.9-4.3 4.1 1 5.8L10 15.9 4.8 17.6l1-5.8L1.5 7.7l5.9-.9z"
                            />
                        </svg>
                    </div>
                    <p class="text-sm text-sage-700">
                        <span class="font-bold text-sage-900">{{ rating }}</span>
                        <span class="text-sage-500"> · средняя оценка</span>
                    </p>
                </div>
            </div>
        </div>
    </section>
</template>
