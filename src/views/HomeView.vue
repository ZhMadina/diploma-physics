<script setup>
  import {useRouter} from "vue-router";

  const router = useRouter()

  router.push({ name: 'content', params: { slug: 'introduction' } })
</script>

<template>
  <main>
    <router-view />
  </main>
</template>
