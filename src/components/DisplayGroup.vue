<template>
  <div class="container">
    <div class="single" v-for="(man, index) in group" :key="index">{{ man }}</div>
  </div>
</template>

<script>
export default {
  name: 'DisplayGroup',
  props: {
    group: Array
  }
}
</script>

<style lang="scss" scoped>
.container {
  width: 12rem;
  height: auto;
  background-color: rgba(245, 245, 245, 0.849);
  border-radius: 0.5rem;
  display: flex;
  flex-direction: column;
  align-items: center;

  .single {
    width: 100%;
    min-height: 4rem;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom: 1px solid black;
    &:last-child {
      border: none;
    }
  }
}
</style>