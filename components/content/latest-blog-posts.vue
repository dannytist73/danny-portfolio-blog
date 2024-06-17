<template>
    <BlogPosts v-slot="{ posts }" :limit="limit">
        <div v-for="post in posts" :key="post.id">
            <NuxtLink :to="post._path">{{ post.title }}</NuxtLink>
        </div>
    </BlogPosts>
</template>

<script setup>
const props = defineProps({
    limit: {
        type: [Number, String],
        default: null,
    },
});

const limit = computed(() => {
    return typeof props.limit === "string"
        ? parseInt(props.limit, 10)
        : props.limit;
});
</script>
