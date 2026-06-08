<script setup>
defineProps({
    eyebrow: { type: String, default: '' },
    title: { type: String, required: true },
    subtitle: { type: String, default: '' },
    align: { type: String, default: 'center' }, // 'center' | 'left'
});
</script>

<template>
    <div
        class="max-w-2xl"
        :class="align === 'center' ? 'mx-auto text-center' : 'text-left'"
    >
        <p
            v-if="eyebrow"
            class="inline-flex items-center gap-2 text-sm font-semibold uppercase tracking-[0.14em] text-sage-600"
        >
            <span class="h-px w-6 bg-sage-300" aria-hidden="true"></span>
            {{ eyebrow }}
        </p>
        <h2
            class="mt-4 font-display text-3xl font-semibold leading-[1.12] tracking-tight text-sage-900 sm:text-4xl"
        >
            {{ title }}
        </h2>
        <p
            v-if="subtitle"
            class="mt-4 text-lg leading-relaxed text-sage-700/80"
            :class="align === 'center' ? 'mx-auto' : ''"
        >
            {{ subtitle }}
        </p>
    </div>
</template>
