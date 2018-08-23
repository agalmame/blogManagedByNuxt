<template>
  <div>
    <TheHeader></TheHeader>
    <main class="main-content">
      <nuxt/>
    </main>
  </div>
</template>
<script>
import TheHeader from '@/components/TheHeader/TheHeader.vue'
export default {
  components:{
    TheHeader
  }
}
</script>

<style>
*{
  box-sizing: border-box
}
body {
  font-family: 'Raleway', Courier, monospace,sans-serif
}
.main-content {
  margin-top: 4.5em;
}
</style>
