<template>
    <div class="flex space-x-2 items-center">
        <div class="text-gray-500 text-xs" v-if="showNextModeLabel">
            Switch to {{ nextMode }} mode
        </div>
        <button @click="toggleMode"
            class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-500 dark:text-gray-400 font-medium"
            @mouseenter="showNextModeLabel = true" @mouseleave="showNextModeLabel = false">
            {{ nextModeIcon }}
        </button>
    </div>
</template>

<script setup>
const showNextModeLabel = ref(false);
const colorMode = useColorMode();

const modes = ["system", "light", "dark"];

const nextModeIcons = {
    system: "⚡",  // or use "☰" or "⚙"
    light: "☀",   // or use "L"
    dark: "☾",    // or use "D"
};

const nextMode = computed(() => {
    const currentModeIndex = modes.indexOf(colorMode.preference);
    let nextModeIndex = null;
    if (currentModeIndex + 1 == modes.length) {
        nextModeIndex = 0;
    } else {
        nextModeIndex = currentModeIndex + 1;
    }

    return modes[nextModeIndex];
});

const nextModeIcon = computed(() => nextModeIcons[nextMode.value]);

const toggleMode = () => (colorMode.preference = nextMode.value);
</script>