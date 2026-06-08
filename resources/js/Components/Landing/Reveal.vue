<script setup>
import { onBeforeUnmount, onMounted, ref } from 'vue';

/**
 * Subtle, accessible fade-up reveal on scroll.
 * Uses IntersectionObserver and fully respects prefers-reduced-motion.
 */
const props = defineProps({
    as: { type: String, default: 'div' },
    delay: { type: Number, default: 0 },
    once: { type: Boolean, default: true },
});

const el = ref(null);
const visible = ref(false);
let observer = null;

onMounted(() => {
    const reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
    if (reduce || !('IntersectionObserver' in window)) {
        visible.value = true;
        return;
    }

    observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    visible.value = true;
                    if (props.once) observer?.unobserve(entry.target);
                } else if (!props.once) {
                    visible.value = false;
                }
            });
        },
        { threshold: 0.15, rootMargin: '0px 0px -10% 0px' },
    );

    if (el.value) observer.observe(el.value);
});

onBeforeUnmount(() => observer?.disconnect());
</script>

<template>
    <component
        :is="as"
        ref="el"
        class="transition-all duration-700 ease-out motion-reduce:transition-none motion-reduce:translate-y-0 motion-reduce:opacity-100"
        :class="visible ? 'translate-y-0 opacity-100' : 'translate-y-8 opacity-0'"
        :style="{ transitionDelay: visible ? `${delay}ms` : '0ms' }"
    >
        <slot />
    </component>
</template>
