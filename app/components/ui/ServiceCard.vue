<template>
  <article
    ref="cardRef"
    class="group relative overflow-hidden rounded-3xl border border-white/70 bg-white p-7 shadow-[0_18px_50px_rgba(3,42,23,0.08)] transition-transform duration-300"
    @mouseenter="handleMouseEnter"
    @mouseleave="handleMouseLeave"
  >
    <div class="pointer-events-none absolute inset-0 bg-gradient-to-br from-white via-white to-[#f4f1ec]" />
    <div class="pointer-events-none absolute -right-10 -top-10 h-32 w-32 rounded-full bg-[#815F53]/10 blur-3xl transition-opacity duration-300 group-hover:opacity-100" />
    <div class="pointer-events-none absolute -bottom-12 -left-10 h-28 w-28 rounded-full bg-[#032A17]/10 blur-3xl transition-opacity duration-300 group-hover:opacity-100" />
    <div class="pointer-events-none absolute inset-x-0 top-0 h-1 bg-gradient-to-r from-[#815F53] via-[#8B6229] to-[#032A17]" />

    <div class="relative z-10">
      <div
        ref="iconRef"
        class="mb-6 inline-flex size-[4.5rem] items-center justify-center rounded-2xl border border-[#815F53]/15 bg-gradient-to-br from-[#815F53]/15 via-white to-[#032A17]/10 text-4xl text-black shadow-[0_12px_30px_rgba(129,95,83,0.15)]"
      >
        <slot name="card-icon" />
      </div>

      <h3 class="mb-3 text-2xl font-bold text-[#141414]">
        <slot name="card-title" />
      </h3>

      <p class="text-base leading-7 text-gray-600">
        <slot />
      </p>

      <a
        href="#"
        class="mt-6 inline-flex items-center gap-2 font-semibold tracking-wide transition-colors duration-300 group-hover:text-[#032A17]"
        style="color: #815F53"
      >
        Learn More
        <span ref="arrowRef" aria-hidden="true">-></span>
      </a>
    </div>
  </article>
</template>

<script setup>
import { gsap } from 'gsap'
import { onBeforeUnmount, onMounted, ref } from 'vue'

const cardRef = ref(null)
const iconRef = ref(null)
const arrowRef = ref(null)

let observer = null
let hasAnimatedIn = false

const handleMouseEnter = () => {
  if (!cardRef.value || !iconRef.value || !arrowRef.value) {
    return
  }

  gsap.to(cardRef.value, {
    y: -10,
    scale: 1.02,
    duration: 0.35,
    ease: 'power2.out',
    boxShadow: '0 28px 60px rgba(3, 42, 23, 0.16)'
  })

  gsap.to(iconRef.value, {
    y: -4,
    rotate: 6,
    scale: 1.08,
    duration: 0.35,
    ease: 'back.out(1.7)'
  })

  gsap.to(arrowRef.value, {
    x: 6,
    duration: 0.25,
    ease: 'power2.out'
  })
}

const handleMouseLeave = () => {
  if (!cardRef.value || !iconRef.value || !arrowRef.value) {
    return
  }

  gsap.to(cardRef.value, {
    y: 0,
    scale: 1,
    duration: 0.35,
    ease: 'power2.out',
    boxShadow: '0 18px 50px rgba(3, 42, 23, 0.08)'
  })

  gsap.to(iconRef.value, {
    y: 0,
    rotate: 0,
    scale: 1,
    duration: 0.35,
    ease: 'power2.out'
  })

  gsap.to(arrowRef.value, {
    x: 0,
    duration: 0.25,
    ease: 'power2.out'
  })
}

onMounted(() => {
  if (!cardRef.value) {
    return
  }

  const content = cardRef.value.querySelectorAll('h3, p, a')

  gsap.set(cardRef.value, {
    autoAlpha: 0,
    y: 32,
    scale: 0.96
  })
  gsap.set(iconRef.value, { autoAlpha: 0, y: 18, scale: 0.85 })
  gsap.set(content, { autoAlpha: 0, y: 18 })

  observer = new IntersectionObserver(
    ([entry]) => {
      if (!entry.isIntersecting || hasAnimatedIn) {
        return
      }

      hasAnimatedIn = true

      const timeline = gsap.timeline({
        defaults: {
          ease: 'power3.out'
        }
      })

      timeline
        .to(cardRef.value, {
          autoAlpha: 1,
          y: 0,
          scale: 1,
          duration: 0.7
        })
        .to(iconRef.value, {
          autoAlpha: 1,
          y: 0,
          scale: 1,
          duration: 0.45
        }, '-=0.4')
        .to(content, {
          autoAlpha: 1,
          y: 0,
          duration: 0.45,
          stagger: 0.08
        }, '-=0.25')

      observer?.disconnect()
    },
    { threshold: 0.25 }
  )

  observer.observe(cardRef.value)
})

onBeforeUnmount(() => {
  observer?.disconnect()
})
</script>
