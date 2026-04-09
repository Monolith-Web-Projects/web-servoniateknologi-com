<template>
    <div class="bg-white p-6 rounded-lg shadow-md hover:shadow-xl transition">
        <div class="w-12 h-12 rounded mb-4 flex items-center justify-center text-black text-xl">
                <slot name="card-icon"></slot>
        </div>
        <h3 class="text-xl md:text-l font-bold mb-2 text-black">
            <slot name="card-title"></slot>
        </h3>
        <p class="text-gray-600">
            <slot></slot>
        </p>
        <a href="#" class="inline-block mt-4" style="color: #815F53">Learn More →</a>
    </div>
</template>