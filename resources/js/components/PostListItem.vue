<template>
    <div class="mb-4">
        <router-link :to="{name: 'post', params: {id: post.id}}">
            <h4
                class="text-2xl pb-3 font-semibold hover:underline"
            >{{ post.title }}</h4>
        </router-link>
        <p class="text-gray-600 pb-3">{{ post.lead }}</p>
        <div class="text-sm text-gray-600">
            By <router-link
                :to="{name: 'author', params: {id: post.author.id}}"
                class="underline hover:text-black"
            >{{ post.author.name }}</router-link> in
            <router-link
                :to="{name: 'topic', params: {slug: post.topic.slug}}"
                class="underline hover:text-black"
            >{{ post.topic.name }}</router-link>
            - {{ post.created_at | timeAgo }}
        </div>
    </div>
</template>

<script>

export default {
    name: "PostListItem",
    props: [
        'post'
    ]
}
</script>

<style scoped>

</style>
