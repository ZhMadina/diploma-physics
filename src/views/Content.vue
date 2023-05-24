<template>
  <div class="WordSection1">
    <div v-html="content.content" :key="content.slug"></div>
  </div>
</template>

<script>
import {useRoute} from "vue-router";
import { ref, watchEffect} from "vue";
import contents from "@/contstants/content.json"

export default {
  name: "Content",
  setup() {
    const route = useRoute()

    const { slug } = route.params

    const content = ref(contents.find((item) => item.slug === slug))

    watchEffect(() => {
      content.value = contents.find((item) => item.slug === route.params.slug)

    })

    return { content }
  }
}
</script>

<style scoped>

</style>
