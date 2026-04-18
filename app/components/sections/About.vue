<template>
 <section class="py-12">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h2 class="text-3xl font-bold mb-4 text-[#032A17] ">
                            <div class="animate-left-to-right">
                                Corporate Tech Innovation
                            </div>
                            <span ref= "GsapSplitChars" class=" bg-gradient-to-r text-[#815F53] gsap-target">You Can Trust</span>
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
                    
                    <!-- Counter -->
                    <UiCounter> </UiCounter>
                </div>
            </div>
        </section>

</template>

<script setup>
import { gsap } from 'gsap'
import SplitText from 'gsap/src/SplitText'
import { onMounted, ref } from 'vue'

// Register GSAP plugin if client-side process
if (process.client) {
  gsap.registerPlugin(SplitText)
}

// target DOM elements
const GsapSplitChars = ref(null)

// State
let split = null
let animation = null

// Setup SplitText
const setupSplitText = () => {
  if (split) {
    split.revert()
  }
  if (animation) {
    animation.revert()
  }
  if (GsapSplitChars.value) {
    split = SplitText.create(GsapSplitChars.value, { type: "chars,words,lines" })
  }
}

// Animation functions
const animateChars = () => {
  if (animation) animation.revert()
  if (!split?.chars) return
  animation = gsap.from(split.chars, {
    x: 150,
    opacity: 0,
    duration: 0.7,
    ease: "power4",
    stagger: 0.04
  })
}

// Setup on Animations 
onMounted(() => {
    setupSplitText()
    //Observer if element is in view then animate chars
    const element = document.querySelector('.gsap-target')
    const observeTitle = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
    if (entry.isIntersecting) {
    // console.log('Element is in view');
    animateChars()
    // animateWords()
    // animateLines()
  }})})
  observeTitle.observe(element)
  // Re-setup on window resize
  window.addEventListener('resize', setupSplitText)


  // Target multiple elements with CSS animations
  const elements = document.querySelectorAll('.animate-fade-right, .animate-fade-up, .animate-scale')
  
  const observeList = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        console.log('Element is in view bro');
        // Add a class to trigger animation
        entry.target.classList.add('animate-in')
        // Stop observing after animation starts
        observeList.unobserve(entry.target)
      }
    })
  }, { threshold: 0.3 }) // Trigger when 30% visible

  // Observe each element
  elements.forEach(element => {
    observeList.observe(element)
  })
})

// Cleanup
onUnmounted(() => {
  window.removeEventListener('resize', setupSplitText)
  if (split) split.revert()
  if (animation) animation.revert()
})
</script>


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

.animate-fade-right.animate-in {
    animation: fadeRight 0.8s ease-out forwards;
}

.animation-delay-200.animate-in {
    animation-delay: 0.2s;
    opacity: 0; /* Start hidden */
}

.animation-delay-400.animate-in {
    animation-delay: 0.4s;
    opacity: 0;
}

.animation-delay-600.animate-in {
    animation-delay: 0.6s;
    opacity: 0;
}
</style>