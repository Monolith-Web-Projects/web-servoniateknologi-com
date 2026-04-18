<template>
    <div class="flex min-h-screen flex-col">
        <!-- Header -->
        <header class="border-b bg-gradient-to-r from-[#1B2D37] to-[#032A17]">
            <UiNavbar />
        </header>

        <!-- Main Content -->
        <main id="main-content" class="flex-1">
            <div class="container-fluid">
                <slot />
            </div>
        </main>

        <!-- Footer -->
        <footer class="py-8" style="background-color: #032A17">
            <UiFooter />
        </footer>
    </div>
</template>