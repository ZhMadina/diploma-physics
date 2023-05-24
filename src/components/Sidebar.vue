<template>
  <div class="sidebar">
    <slot />
  </div>
</template>

<script>
export default {
  name: "Sidebar"
}
</script>

<style scoped lang="scss">
  .sidebar {
    min-width: 300px;
    max-width: 300px;
    float: left;
    height: 100vh;
    background: rgb(245,246,247);
    border: 1px solid rgb(196,203,208);
    position: sticky;
    top: 0;
    overflow-y: auto;
    border-radius: 8px 0 0 8px;
    padding: 16px 0;
  }
</style>
