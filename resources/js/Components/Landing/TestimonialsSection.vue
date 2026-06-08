<script setup>
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const testimonials = [
    {
        quote: 'Я не ждала чудес, просто хотела перестать засыпать после обеда. К третьему дню заметила, что днём больше не «выключаюсь» — и впервые за долгое время утро перестало быть мучением.',
        name: 'Марина',
        meta: '38 лет',
        avatar: 'https://i.pravatar.cc/120?img=47',
        topic: 'Энергия',
    },
    {
        quote: 'Самое ценное — это про вздутие и тяжесть. Я думала, что у меня просто «такой живот». Оказалось, дело в нескольких привычках. Сейчас после еды реально легче, без дискомфорта к вечеру.',
        name: 'Ольга',
        meta: '45 лет',
        avatar: 'https://i.pravatar.cc/120?img=31',
        topic: 'Пищеварение',
    },
    {
        quote: 'Понравилось, что без фанатизма и запретов. Простые утренние ритуалы я делаю до сих пор — они заняли минут десять, а вошли в жизнь насовсем. Питание стало понятным, без вечных сомнений.',
        name: 'Дмитрий',
        meta: '34 года',
        avatar: 'https://i.pravatar.cc/120?img=13',
        topic: 'Привычки',
    },
];
</script>

<template>
    <section
        id="testimonials"
        aria-labelledby="testimonials-heading"
        class="relative bg-cream-100 py-20 sm:py-28"
    >
        <div class="mx-auto w-full max-w-7xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="Отзывы участников"
                    title="Небольшие изменения — заметная разница"
                    subtitle="Реальные истории про то, как меняется самочувствие, когда появляется понятная система."
                />
                <h2 id="testimonials-heading" class="sr-only">Отзывы</h2>
            </Reveal>

            <ul role="list" class="mt-14 grid gap-6 lg:grid-cols-3">
                <Reveal
                    v-for="(item, i) in testimonials"
                    :key="item.name"
                    as="li"
                    :delay="i * 120"
                >
                    <figure
                        class="flex h-full flex-col rounded-3xl border border-sage-100 bg-white/80 p-7 shadow-sm shadow-sage-900/5 backdrop-blur-sm"
                    >
                        <span
                            class="font-display text-5xl leading-none text-sage-200"
                            aria-hidden="true"
                            >&ldquo;</span
                        >
                        <blockquote
                            class="-mt-3 flex-1 text-base leading-relaxed text-sage-800"
                        >
                            {{ item.quote }}
                        </blockquote>
                        <figcaption
                            class="mt-6 flex items-center gap-3 border-t border-sage-100 pt-5"
                        >
                            <img
                                :src="item.avatar"
                                :alt="`Участница интенсива ${item.name}`"
                                class="h-11 w-11 rounded-full object-cover ring-2 ring-white"
                                loading="lazy"
                                decoding="async"
                            />
                            <div class="flex-1">
                                <p class="text-sm font-semibold text-sage-900">
                                    {{ item.name }}
                                    <span class="font-normal text-sage-500"
                                        >· {{ item.meta }}</span
                                    >
                                </p>
                                <p class="text-xs text-sage-500">
                                    Участник интенсива
                                </p>
                            </div>
                            <span
                                class="rounded-full bg-sage-100 px-3 py-1 text-xs font-medium text-sage-700"
                            >
                                {{ item.topic }}
                            </span>
                        </figcaption>
                    </figure>
                </Reveal>
            </ul>
        </div>
    </section>
</template>
