<script setup>
import { ref } from 'vue';
import Reveal from '@/Components/Landing/Reveal.vue';
import SectionHeading from '@/Components/Landing/SectionHeading.vue';

const faqs = [
    {
        q: 'Подойдёт ли интенсив новичкам?',
        a: 'Да. Мы объясняем всё простым языком и не предполагаем никакой подготовки. Если вы только начинаете интересоваться здоровьем, питанием и привычками — вам будет комфортно. Опытным участникам мы поможем собрать знания в понятную систему.',
    },
    {
        q: 'Нужно ли покупать специальные продукты?',
        a: 'Нет. Все рецепты построены на доступных продуктах, которые есть в обычном магазине. Никаких редких добавок, экзотических суперфудов или дорогих покупок — только простые и привычные ингредиенты.',
    },
    {
        q: 'Будут ли записи эфиров?',
        a: 'Да. Все живые эфиры сохраняются, и у вас будет доступ к записям. Если не получится присутствовать онлайн, вы спокойно посмотрите материал в удобное время и ничего не пропустите.',
    },
    {
        q: 'Что делать, если у меня проблемы с ЖКТ?',
        a: 'Интенсив носит образовательный характер и помогает выстроить бережные привычки. Это не замена консультации врача: при хронических заболеваниях или обострениях сначала стоит проконсультироваться со специалистом, а практики применять мягко и по самочувствию.',
    },
    {
        q: 'Сколько времени займут практики?',
        a: 'Утренние практики занимают около 10–20 минут. Они построены так, чтобы легко вписываться в обычное утро — даже в будний день перед работой. Никакой многочасовой нагрузки не будет.',
    },
];

const open = ref(0);
function toggle(index) {
    open.value = open.value === index ? -1 : index;
}
</script>

<template>
    <section
        id="faq"
        aria-labelledby="faq-heading"
        class="relative bg-cream-50 py-20 sm:py-28"
    >
        <div class="mx-auto w-full max-w-3xl px-5 sm:px-8">
            <Reveal>
                <SectionHeading
                    eyebrow="Вопросы и ответы"
                    title="Отвечаем на частые вопросы"
                    subtitle="Если остались сомнения — здесь самое важное о том, как проходит интенсив."
                />
                <h2 id="faq-heading" class="sr-only">Частые вопросы</h2>
            </Reveal>

            <Reveal :delay="100">
                <dl class="mt-12 space-y-4">
                    <div
                        v-for="(faq, i) in faqs"
                        :key="faq.q"
                        class="overflow-hidden rounded-2xl border border-sage-100 bg-white/80 shadow-sm shadow-sage-900/5 backdrop-blur-sm transition-colors"
                        :class="open === i ? 'border-sage-200' : ''"
                    >
                        <dt>
                            <button
                                type="button"
                                class="flex w-full items-center justify-between gap-4 px-6 py-5 text-left transition-colors hover:bg-sage-50/50 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-[-2px] focus-visible:outline-sage-600"
                                :aria-expanded="open === i"
                                :aria-controls="`faq-panel-${i}`"
                                :id="`faq-button-${i}`"
                                @click="toggle(i)"
                            >
                                <span
                                    class="text-base font-semibold text-sage-900 sm:text-lg"
                                >
                                    {{ faq.q }}
                                </span>
                                <span
                                    class="flex h-8 w-8 flex-none items-center justify-center rounded-full bg-sage-100 text-sage-600 transition-transform duration-300"
                                    :class="open === i ? 'rotate-45' : ''"
                                    aria-hidden="true"
                                >
                                    <svg
                                        class="h-4 w-4"
                                        viewBox="0 0 20 20"
                                        fill="none"
                                        stroke="currentColor"
                                        stroke-width="2.2"
                                        stroke-linecap="round"
                                    >
                                        <path d="M10 4v12M4 10h12" />
                                    </svg>
                                </span>
                            </button>
                        </dt>
                        <dd
                            :id="`faq-panel-${i}`"
                            role="region"
                            :aria-labelledby="`faq-button-${i}`"
                            class="grid transition-all duration-300 ease-out motion-reduce:transition-none"
                            :class="
                                open === i
                                    ? 'grid-rows-[1fr] opacity-100'
                                    : 'grid-rows-[0fr] opacity-0'
                            "
                        >
                            <div class="overflow-hidden">
                                <p
                                    class="px-6 pb-5 text-base leading-relaxed text-sage-700/85"
                                >
                                    {{ faq.a }}
                                </p>
                            </div>
                        </dd>
                    </div>
                </dl>
            </Reveal>
        </div>
    </section>
</template>
