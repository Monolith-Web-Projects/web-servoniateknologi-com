<script setup>
    const titleMain = ref("SERVONIATEKNOLOGI")
    const titleDesc = ref("Innovation You Can Trust.")
    const desc = ref("Corporate tech solutions delivering innovation and reliability for modern businesses.")
</script>

<template>
    <section class="relative pt-24 pb-12 overflow-hidden">
        <!-- Background Image -->
        <div class="absolute inset-0 z-0">
            <img src="~/assets/images/Hero_Banner.png" alt="Hero Background" class="w-full h-full object-cover" />
            <!-- Optional: Dark overlay for better text readability -->
            <div class="absolute inset-0 bg-black/40"></div>
        </div>

        <!-- Content -->
        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div id="hero-desc" class="text-center">
                <h1 id="hero-title-h1"
                    class="text-4xl md:text-6xl md:text-center text-left font-bold mb-4 text-white break-words animate-fade-up ">
                    {{titleMain}}
                </h1>
                <h2 id="hero-title-h2" class="text-4xl md:text-6xl md:text-center text-left font-bold mb-4 text-white animate-fade-up animation-delay-200">
                    {{titleDesc}}
                </h2>
                <p id="hero-title-p" class="text-xl text-white/90 mb-8 max-w-2xl mx-auto animate-fade-up animation-delay-400">
                    {{desc}}
                </p>
                <button class="px-6 py-3 rounded text-white transition transform hover:scale-105 hover:bg-opacity-90"
                    style="background-color: #815F53">
                    Learn More
                </button>
            </div>
        </div>
    </section>
</template>

<style scoped>
    #hero-title-h1 {
        font-family: 'GoogleSans', 'Roboto', sans-serif;
        font-weight: 900;
    }

    #hero-title-h2 {
        font-family: 'GoogleSans', 'Roboto', sans-serif;
        font-weight: 900;
    }

    #hero-title-p {
        font-family: 'GoogleSans', 'Roboto', sans-serif;
        font-weight: 400;
    }

    @media (min-width: 768px) {
        #hero-title-h1 {
            font-size: 6rem;
        }

        #hero-title-h2 {
            font-size: 4rem;
        }
    }

    /* Animation Handling */
    /* Fade Up Animation */
@keyframes fadeUp {
    from {
        opacity: 0;
        transform: translateY(30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animate-fade-up {
    animation: fadeUp 0.8s ease-out forwards;
}

.animation-delay-200 {
    animation-delay: 0.2s;
    opacity: 0; /* Start hidden */
}

.animation-delay-400 {
    animation-delay: 0.4s;
    opacity: 0;
}

.animation-delay-600 {
    animation-delay: 0.6s;
    opacity: 0;
}
</style>