<template>
    <div class="mx-full flex items-center justify-between py-4 px-4 md:px-8 relative">
        <h2 class="text-xl font-bold text-white">ServoniaTek</h2>

        <!-- Desktop Menu -->
        <nav class="hidden md:flex space-x-6">
            <a href="#" class="text-white hover:text-blue-600 transition-colors">Home</a>
            <a href="#" class="text-white hover:text-blue-600 transition-colors">Services</a>
            <a href="#" class="text-white hover:text-blue-600 transition-colors">About</a>
            <a href="#" class="text-white hover:text-blue-600 transition-colors">Contact</a>
        </nav>

        <!-- Mobile Menu Button -->
        <button
            @click="toggleMenu"
            class="md:hidden p-2 rounded-lg hover:bg-white/10 text-white"
        >
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
                <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
            </svg>
        </button>

        <!-- Mobile Menu with Fade + Slide Effect -->
        <Transition name="fade-slide">
            <div
                v-if="isMenuOpen"
                class="absolute top-16 left-0 right-0 bg-gradient-to-r from-[#1B2D37] to-[#032A17] shadow-lg md:hidden z-50 rounded-b-lg"
            >
                <nav class="flex flex-col space-y-4 p-4">
                    <a href="#" class="text-white hover:text-blue-600 transition-colors py-2 px-4 hover:bg-white/10 rounded-lg">Home</a>
                    <a href="#" class="text-white hover:text-blue-600 transition-colors py-2 px-4 hover:bg-white/10 rounded-lg">Services</a>
                    <a href="#" class="text-white hover:text-blue-600 transition-colors py-2 px-4 hover:bg-white/10 rounded-lg">About</a>
                    <a href="#" class="text-white hover:text-blue-600 transition-colors py-2 px-4 hover:bg-white/10 rounded-lg">Contact</a>
                </nav>
            </div>
        </Transition>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value
}
</script>

<style scoped>
/* Fade + Slide animation */
.fade-slide-enter-active,
.fade-slide-leave-active {
    transition: all 0.3s ease;
}

.fade-slide-enter-from,
.fade-slide-leave-to {
    opacity: 0;
    transform: translateY(-10px);
}

.fade-slide-enter-to,
.fade-slide-leave-from {
    opacity: 1;
    transform: translateY(0);
}
</style>
