<template>
  <div class="container text-black">
    <div class="button-wrapper">
      <button ref="charsBtn" class="button">Characters</button>
      <button ref="wordsBtn" class="button">Words</button>
      <button ref="linesBtn" class="button">Lines</button>
    </div>
    <div ref="textRef" class="text">
      Break apart HTML text into characters, words, and/or lines for easy animation.
    </div>
  </div>
</template>

<script setup>
import { gsap } from 'gsap'
import SplitText from 'gsap/src/SplitText'
import { onMounted, ref } from 'vue'

// Register GSAP plugin
if (process.client) {
  gsap.registerPlugin(SplitText)
}

// Refs for DOM elements
const = ref(null)
const wordsBtn = ref(null)
const linesBtn = ref(null)
const textRef = ref(null)

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
  if (textRef.value) {
    split = SplitText.create(textRef.value, { type: "chars,words,lines" })
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

const animateWords = () => {
  if (animation) animation.revert()
  if (!split?.words) return
  animation = gsap.from(split.words, {
    y: -100,
    opacity: 0,
    rotation: "random(-80, 80)",
    duration: 0.7,
    ease: "back",
    stagger: 0.15
  })
}

const animateLines = () => {
  if (animation) animation.revert()
  if (!split?.lines) return
  animation = gsap.from(split.lines, {
    rotationX: -100,
    transformOrigin: "50% 50% -160px",
    opacity: 0,
    duration: 0.8,
    ease: "power3",
    stagger: 0.25
  })
}

// Setup on client-side only
onMounted(() => {
  setupSplitText()
  
  // Add event listeners
  charsBtn.value?.addEventListener('click', animateChars)
  wordsBtn.value?.addEventListener('click', animateWords)
  linesBtn.value?.addEventListener('click', animateLines)
  
  // Re-setup on window resize
  window.addEventListener('resize', setupSplitText)
})

// Cleanup
onUnmounted(() => {
  charsBtn.value?.removeEventListener('click', animateChars)
  wordsBtn.value?.removeEventListener('click', animateWords)
  linesBtn.value?.removeEventListener('click', animateLines)
  window.removeEventListener('resize', setupSplitText)
  if (split) split.revert()
  if (animation) animation.revert()
})
</script>

<style scoped>
.container {
  padding: 2rem;
}

.button-wrapper {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}

.button {
  padding: 0.5rem 1rem;
  background-color: #815F53;
  color: white;
  border: none;
  border-radius: 0.5rem;
  cursor: pointer;
  transition: transform 0.2s;
}

.button:hover {
  transform: scale(1.05);
}

.text {
  font-size: 1.25rem;
  line-height: 1.6;
  max-width: 600px;
}
</style>