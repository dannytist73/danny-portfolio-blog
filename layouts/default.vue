<template>
    <div class="min-h-screen bg-white dark:bg-gray-900">
        <div class="container mx-auto max-w-4xl px-4">
            <header class="flex justify-between items-start md:items-center pt-5">
                <div class="flex items-center md:space-x-12">
                    <div class="hidden md:block">
                        <NuxtLink to="/" class="text-xl font-semibold p-2 hover:bg-gray-200 dark:hover:bg-gray-500">
                            dannytist.dev
                        </NuxtLink>
                    </div>
                    <Menu />
                </div>

                <ClientOnly>
                    <ColorModeSelector />
                </ClientOnly>
            </header>
            <main class="py-10">
                <slot />
            </main>
        </div>
    </div>
</template>

<script setup lang="ts">
useHead({
    titleTemplate: "%s - D-Code Portfolio Journal",
    link: [
        {
            rel: "preconnect",
            href: "https://fonts.googleapis.com",
        },
        {
            rel: "stylesheet",
            href: "https://fonts.googleapis.com/css2?family=Roboto&display=swap",
            crossorigin: "",
        },
    ],
});
</script>

<style>
body {
    font-family: Roboto;
}

body {
    @apply bg-white dark:bg-gray-900 text-gray-700 dark:text-gray-300;
}
</style>
