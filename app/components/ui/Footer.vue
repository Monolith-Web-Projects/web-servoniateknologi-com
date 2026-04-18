<template>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="grid md:grid-cols-3 gap-8">
                    <div>
                        <h3 class="font-bold text-white mb-3">{{ titleMain }}</h3>
                        <p class="text-gray-400 text-sm">{{ titleDesc }}</p>
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
                            <li>{{ textEmailContact }}</li>
                            <li>Jakarta, Indonesia</li>
                        </ul>
                    </div>
                </div>

                <div class="border-t border-gray-800 mt-8 pt-6 text-center text-gray-400 text-sm">
                    <p>&copy; {{textCopyRight}}</p>
                </div>
            </div>
</template>
<script setup>
const textCopyRight = ref('2026 SERVONIATEKNOLOGI. All rights reserved.')
const textEmailContact = ref('hello@servoniateknologi.com')
const titleMain = ref('SERVONIATEKNOLOGI')
const titleDesc = ref('Innovation You Can Trust')
</script>