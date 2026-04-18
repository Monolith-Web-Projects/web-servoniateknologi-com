<template>
    <section class="py-12 bg-gray-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-bold text-center mb-10 text-black">Our Services</h2>
            <div class="mb-10 flex items-center justify-center gap-4 text-[#032A17]">
            </div>

            <div class="grid md:grid-cols-3 gap-6">
                <!-- Service 1 -->
                <UiServiceCard>
                    <template #card-icon>
                        <span class="inline-flex items-center justify-center">
                            <Computer />
                        </span>
                    </template>
                    <template #card-title>Software Solutions</template>
                    Neat your unios or professoris conversustur adipiscing elit.
                </UiServiceCard>

                <!-- Service 2 -->
                <UiServiceCard>
                    <template #card-icon>
                        <span class="inline-flex items-center justify-center">
                            <Globe />
                        </span>
                    </template>
                    <template #card-title>Consulting</template>
                    Expert consulting to deliver optimal solutions for your business.
                </UiServiceCard>
                <!-- Service 3 -->
                <UiServiceCard>
                    <template #card-icon>
                        <span class="inline-flex items-center justify-center">
                            <ShieldCheck />
                        </span>
                    </template>
                    <template #card-title>Security</template>
                    Enterprise-grade security solutions to protect your business.
                </UiServiceCard>

            </div>
        </div>
    </section>
</template>

<script setup>
import { UIcon } from '#components'
import { h } from 'vue'

const iconClass = 'size-10 text-[#69473B]'

const Computer = () => h(UIcon, { name: 'i-lucide-computer', class: iconClass })
const Globe = () => h(UIcon, { name: 'i-lucide-globe', class: iconClass })
const ShieldCheck = () => h(UIcon, { name: 'i-lucide-shield-check', class: iconClass })
</script>
