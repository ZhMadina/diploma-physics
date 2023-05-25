<template>
  <main>
    <div class="main-title">
      <h1>Электр және магнетизм</h1>
    </div>
    <img src="https://images.newscientist.com/wp-content/uploads/2020/08/26150002/electromagnetsim-fyckc9_web.jpg?width=1200" alt="">
  </main>
</template>

<script setup>

</script>

<style lang="scss">
main {
  position: relative;
  .main-title {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: grid;
    place-content: center;
    z-index: 1;
    background: rgba(0,0,0,0.4);
    h1 {
      margin: 0;
      color: #FFFFFF;
      font-size: 36px !important;
    }
  }

  img {
    max-width: 100%;
  }
}

</style>
