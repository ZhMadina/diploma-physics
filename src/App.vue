

<template>
    <div>
      <div class="container">
        <div class="app-layout">
          <div class="app-layout__sidebar">
            <Sidebar>
              <SidebarLinks :node="node" v-for="node in sidebar" :key="node.id" />
            </Sidebar>
          </div>
          <div class="app-layout__content">
            <RouterView />
          </div>
        </div>
      </div>
    </div>
</template>

<script setup>
import { RouterView } from 'vue-router'
import Sidebar from "@/components/Sidebar.vue";
import SidebarLinks from "@/components/SidebarLinks.vue";
import sidebar from "@/contstants/sidebar.json";
</script>

<style scoped lang="scss">
.app-layout {
  display: flex;
  &__content {
    padding: 16px 24px;
  }
}
</style>
