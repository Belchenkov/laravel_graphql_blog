<template>
    <div class="container mx-auto px-4 w-full md:w-3/4 lg:w-3/5 xl:w-1/2 my-20">
        <h2 class="text-4xl">
            <router-link
                :to="{name: 'index'}"
                class="text-gray-600 hover:underline"
            >All Posts</router-link>
            <span class="text-gray-600">/</span>
            <template v-if="topic">{{ topic.name }}</template>
        </h2>
        <div v-if="$apollo.loading">Loading ...</div>
        <div v-else>
            <PostListItem
                v-for="post in topic.posts"
                :key="post.id"
                :post="post"
            />
        </div>
    </div>
</template>

<script>
import gql from "graphql-tag";
import PostListItem from "../components/PostListItem";

export default {
    name: "TopicList",
    components: {
        PostListItem
    },
    apollo: {
        topic: {
            query: gql`query($slug: String!) {
                topic(slug: $slug) {
                    id
                    name
                    posts {
                        id
                        title
                        lead
                        created_at
                        author {
                            id
                            name
                        }
                        topic {
                            name
                            slug
                        }
                    }
                }
            }`,
            variables() {
                return {
                    slug: this.$route.params.slug
                };
            }
        }
    }
}
</script>

<style scoped>

</style>
