<template>
    <div ref="elementRef" class="bg-gray-100 p-8 rounded-lg" style="background-color: #032A17">
        <div class="text-center text-white">
            <div class="text-5xl font-bold mb-2">{{ projectCount }}</div>
            <div class="text-lg">Projects Completed</div>
            <div class="mt-6 pt-6 border-t border-white/20">
                <div class="text-3xl font-bold">{{ satisfactionCount }}%</div>
                <div>Client Satisfaction</div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed, ref } from 'vue'
import { useIntersectionObserver, useTransition } from '@vueuse/core'

// Track if animation has started
const hasStarted = ref(false)
const elementRef = ref(null)
const projectTarget = ref(0)
const satisfactionTarget = ref(0)

// Smoothly animate displayed values toward the target numbers.
const animatedProjects = useTransition(projectTarget, {
  duration: 1800
})
const animatedSatisfaction = useTransition(satisfactionTarget, {
  duration: 1800
})

const projectCount = computed(() => Math.round(animatedProjects.value))
const satisfactionCount = computed(() => Math.round(animatedSatisfaction.value))

// Start counting when element becomes visible
useIntersectionObserver(
  elementRef,
  ([{ isIntersecting }]) => {
    if (isIntersecting && !hasStarted.value) {
      hasStarted.value = true
      projectTarget.value = 500
      satisfactionTarget.value = 98
    }
  },
  { threshold: 0.3 }
)
</script>
