<template>
  <div class="container">
    <CryptoItemList />
  </div>
</template>

<script>
import CryptoItemList from '@/components/CryptoItemList'
export default {
  name: 'Main',
  components: {
    CryptoItemList,
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  flex-direction: column;
}
</style>
