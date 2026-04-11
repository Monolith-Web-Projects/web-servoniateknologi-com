<template>
 <section class="py-12">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h2 class="text-3xl font-bold mb-4 text-[#032A17] ">
                            <div class="animate-left-to-right">

                                Corporate Tech Innovation
                            </div>
                            <span class=" bg-gradient-to-r text-[#815F53] animate-right-to-left">You Can Trust</span>
                        </h2>
                        <p class="text-gray-600 mb-4">
                            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut
                            labore et dolore magna aliquat.
                        </p>
                        <div class="space-y-2 text-[#141414]">
                            <div class="flex items-center gap-2 animate-fade-right animation-delay-200">
                                <svg class="w-5 h-5" style="color: #69473B" fill="currentColor" viewBox="0 0 20 20">
                                    <path fill-rule="evenodd"
                                        d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                                        clip-rule="evenodd" />
                                </svg>
                                <span>Enterprise Solutions</span>
                            </div>
                            <div class="flex items-center gap-2 animate-fade-right animation-delay-400">
                                <svg class="w-5 h-5" style="color: #69473B" fill="currentColor" viewBox="0 0 20 20">
                                    <path fill-rule="evenodd"
                                        d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                                        clip-rule="evenodd" />
                                </svg>
                                <span>24/7 Support</span>
                            </div>
                            <div class="flex items-center gap-2 animate-fade-right animation-delay-600">
                                <svg class="w-5 h-5" style="color: #69473B" fill="currentColor" viewBox="0 0 20 20">
                                    <path fill-rule="evenodd"
                                        d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                                        clip-rule="evenodd" />
                                </svg>
                                <span>Global Reach</span>
                            </div>
                        </div>
                    </div>

                    <div class="bg-gray-100 p-8 rounded-lg" style="background-color: #032A17">
                        <div class="text-center text-white">
                            <div class="text-5xl font-bold mb-2">500+</div>
                            <div class="text-lg">Projects Completed</div>
                            <div class="mt-6 pt-6 border-t border-white/20">
                                <div class="text-3xl font-bold">98%</div>
                                <div>Client Satisfaction</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

</template>

<style scoped>
/* fade right */
@keyframes fadeRight {
    from {
        opacity: 0;
        transform: translateX(-30px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animate-fade-right {
    animation: fadeRight 0.8s ease-out forwards;
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

@keyframes lefttoRight {
    from {
        opacity:0;
        transform: translateX(-100px)
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animate-left-to-right {
    animation: lefttoRight 0.5s ease-in forwards
}


@keyframes RighttoLeft {
    from {
        opacity:0;
        transform: translateX(100px)
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.animate-right-to-left {
    animation: RighttoLeft 0.5s ease-in forwards
}

</style>