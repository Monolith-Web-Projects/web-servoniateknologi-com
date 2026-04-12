<template>
    <div ref="elementRef" class="bg-gray-100 p-8 rounded-lg" style="background-color: #032A17">
        <div class="text-center text-white">
            <div class="text-5xl font-bold mb-2">{{projectCounts}}</div>
            <div class="text-lg">Projects Completed</div>
            <div class="mt-6 pt-6 border-t border-white/20">
                <div class="text-3xl font-bold">{{satisfactionCounts}}%</div>
                <div>Client Satisfaction</div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useCounter } from '@vueuse/core';
import { useIntersectionObserver } from '@vueuse/core'


// const projectCount = ref(500)
// const clientSatisfaction = ref(98)

const projectCounter = useCounter(0, {min: 0, max: 500})
const satisfactionCounter = useCounter(0, {min: 0, max: 100})

// Track if animation has started
const hasStarted = ref(false)
const elementRef = ref(null)

// Start counting when element becomes visible
useIntersectionObserver(
    elementRef,
    ([{ isIntersecting }]) => {
        if (isIntersecting && !hasStarted.value) {
            hasStarted.value = true
            projectCounter.set(500) // This will animate to 500
            satisfactionCounter.set(98) // This will animate to 98
        }
    },
    { threshold: 0.3 } // Start when 30% of element is visible
)

const projectCounts = projectCounter.counter
const satisfactionCounts = satisfactionCounter.counter


</script>
