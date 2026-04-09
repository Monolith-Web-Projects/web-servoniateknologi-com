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

        <!-- Footer -->
        <footer class="py-8" style="background-color: #032A17">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid md:grid-cols-3 gap-8">
                    <div>
                        <h3 class="font-bold text-white mb-3">SERVONIATEKNOLOGI</h3>
                        <p class="text-gray-400 text-sm">Innovation You Can Trust</p>
                    </div>

                    <div>
                        <h4 class="font-bold text-white mb-3">Quick Links</h4>
                        <ul class="space-y-1 text-sm text-gray-400">
                            <li><a href="#" class="hover:text-white">Home</a></li>
                            <li><a href="#" class="hover:text-white">Services</a></li>
                            <li><a href="#" class="hover:text-white">About</a></li>
                        </ul>
                    </div>

                    <div>
                        <h4 class="font-bold text-white mb-3">Contact</h4>
                        <ul class="space-y-1 text-sm text-gray-400">
                            <li>hello@servoniateknologi.com</li>
                            <li>Jakarta, Indonesia</li>
                        </ul>
                    </div>
                </div>

                <div class="border-t border-gray-800 mt-8 pt-6 text-center text-gray-400 text-sm">
                    <p>&copy; 2026 SERVONIATEKNOLOGI. All rights reserved.</p>
                </div>
            </div>
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