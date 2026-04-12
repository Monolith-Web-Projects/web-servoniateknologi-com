<template>
    <div class="min-h-screen bg-white">
        <!-- Hero Section -->
        <sectionsHero></sectionsHero>
        <!-- Services Section -->
        <SectionsServices></SectionsServices>

        <!-- About Section -->
        <SectionsAbout></SectionsAbout>

        <!-- CTA Section -->
        <SectionsCta></SectionsCta>

        <!-- Test Section -->
        <!-- <ui-test></ui-test> -->
        
        <!-- Footer -->
        <footer class="py-8" style="background-color: #032A17">
            <UiFooter></UiFooter>
        </footer>
    </div>
</template>

<script setup>
import { components } from '@vue/language-core/lib/codegen/names';

    // No additional code needed - this is a static homepage
</script>

<style scoped>
    /* Smooth hover transitions */
    button,
    a {
        transition: all 0.3s ease;
    }

    button:hover {
        transform: translateY(-2px);
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    }
</style>