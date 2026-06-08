<script setup>
import { Head } from '@inertiajs/vue3';
import HeroSection from '@/Components/HeroSection.vue';
import ProblemsSection from '@/Components/Landing/ProblemsSection.vue';
import ResultsSection from '@/Components/Landing/ResultsSection.vue';
import ProgramSection from '@/Components/Landing/ProgramSection.vue';
import MorningPracticeSection from '@/Components/Landing/MorningPracticeSection.vue';
import FormatSection from '@/Components/Landing/FormatSection.vue';
import ExpertSection from '@/Components/Landing/ExpertSection.vue';
import TestimonialsSection from '@/Components/Landing/TestimonialsSection.vue';
import FAQSection from '@/Components/Landing/FAQSection.vue';
import PricingSection from '@/Components/Landing/PricingSection.vue';
import FinalCTASection from '@/Components/Landing/FinalCTASection.vue';

defineProps({
    startDate: { type: String, default: '[дата интенсива]' },
    price: { type: String, default: '990 ₽' },
});

function scrollToRegister() {
    document
        .getElementById('register')
        ?.scrollIntoView({ behavior: 'smooth', block: 'start' });
}
</script>

<template>
    <Head>
        <title>3-дневный интенсив о здоровье, питании и энергии</title>
        <meta
            name="description"
            content="Премиальный онлайн-интенсив за 3 дня: утренние ритуалы, питание и здоровье ЖКТ для стабильной энергии и хорошего самочувствия. Старт скоро — участие 990 ₽."
        />
    </Head>

    <div class="min-h-screen bg-cream-50 font-sans text-sage-900 antialiased">
        <main>
            <!-- 1. First screen -->
            <HeroSection
                :start-date="startDate"
                :price="price"
                cta-href="#register"
                @cta="scrollToRegister"
            />

            <!-- 2. Recognition: see yourself in the problem -->
            <ProblemsSection />

            <!-- 3. Desire: paint the outcome -->
            <ResultsSection />

            <!-- 4. Mechanism: the 3-day program -->
            <ProgramSection />

            <!-- 5. Experience: what mornings look like -->
            <MorningPracticeSection />

            <!-- 6. Reassurance: simple, accessible format -->
            <FormatSection />

            <!-- 7. Authority: the expert -->
            <ExpertSection />

            <!-- 8. Social proof -->
            <TestimonialsSection />

            <!-- 9. Objection handling -->
            <FAQSection />

            <!-- 10. Offer -->
            <PricingSection
                :price="price"
                :start-date="startDate"
                cta-href="#register"
                @cta="scrollToRegister"
            />

            <!-- 11. Final call to action -->
            <FinalCTASection :start-date="startDate" />
        </main>

        <footer class="bg-sage-900 py-10 text-center text-sm text-cream-100/70">
            <div class="mx-auto max-w-7xl px-5 sm:px-8">
                <p>3-дневный онлайн-интенсив о здоровье и энергии</p>
                <p class="mt-2 text-cream-100/50">
                    Материалы носят образовательный характер и не заменяют
                    консультацию врача.
                </p>
            </div>
        </footer>
    </div>
</template>
