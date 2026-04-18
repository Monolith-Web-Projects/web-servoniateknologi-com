<template>
    <section class="relative overflow-hidden pt-20 pb-14 sm:pt-24 sm:pb-16">
        <!-- Background Image -->
        <div class="absolute inset-0 z-0">
            <img src="~/assets/images/Hero_Banner.png" alt="Hero Background" class="w-full h-full object-cover" />
            <!-- Optional: Dark overlay for better text readability -->
            <div class="absolute inset-0 bg-black/40"></div>
        </div>

        <!-- Content -->
        <div id="hero-desc" class="relative z-10 mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 select-none text-center">
                <h1 id="hero-title-h1"
                    class="mb-3 text-left text-[2rem] leading-[1.05] font-bold text-balance text-white animate-fade-up sm:text-center sm:text-[2.75rem] md:mb-4 md:text-[4.5rem] break-all">
                    {{ titleMain }}
                </h1>
                <h2
                    id="hero-title-h2"
                    class="font-bold mb-4 text-left text-[1.6rem] leading-[1.1]  text-white animate-fade-up animation-delay-200 sm:text-center sm:text-[2.25rem] md:text-[3.5rem]"
                >
                    {{ titleDesc }}
                </h2>
                <p
                    id="hero-title-p"
                    class="mx-0 mb-8 max-w-xl text-left text-base leading-7 text-white/90 animate-fade-up animation-delay-400 sm:mx-auto sm:text-center sm:text-lg md:max-w-2xl md:text-xl"
                >
                    {{ desc }}
                </p>
                <button class="rounded px-6 py-3 text-white transition transform hover:scale-105 hover:bg-opacity-90"
                    style="background-color: #815F53">
                    Learn More
                </button>
        </div>
    </section>
</template>

<script setup>
    const titleMain = ref("SERVONIATEKNOLOGI")
    const titleDesc = ref("Innovation You Can Trust")
    const desc = ref("Corporate tech solutions delivering innovation and reliability for modern businesses.")
</script>

<style scoped>
    #hero-title-h1 {
        font-family: 'GoogleSans', 'Roboto', sans-serif;
        font-weight: 900;
        text-wrap: balance;
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
