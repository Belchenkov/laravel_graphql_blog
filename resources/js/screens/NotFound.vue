<template>
    <div class="h-screen w-screen bg-gray-200 flex justify-center">
        <div class="text-center self-center text-gray-600">
            <h1 class="text-6xl text-shadow">404</h1>
            <h3 class="text-4xl text-shadow">This page can not be found!</h3>
        </div>
        <div class="absolute bottom-0 mb-12 text-gray-600 text-center text-xl">
            <span class="opacity-50">Take me back to</span>
            <a href="#" class="border-b" @click="$router.go(-1)">where I was</a>
        </div>
    </div>
</template>

<script>
export default {
    name: "NotFound"
}
</script>

<style scoped>

</style>
