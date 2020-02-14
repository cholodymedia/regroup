<template>
  <div class="container">
    <div class="name">
      {{name}}
    </div>
    <div class="delete">
      <font-awesome-icon :icon="['fas', 'plus-circle']" class="button" @click="clickDelete"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DisplayUser',
  props: {
    name: String,
    id: Number
  },
  methods: {
    clickDelete() {
      this.$emit('delete', this.id);
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  width: 12rem;
  height: 3rem;
  display: flex;
  flex-direction: row;
  background-color: rgba(245, 245, 245, 0.849);
  border-radius: 0.5rem;

  .name {
    flex: 4;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .delete {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;

    .button {
      font-size: 1.4rem;
      transform: rotate(45deg);
      color: rgb(168, 37, 37);

      &:hover {
        cursor: pointer;
        color: rgb(204, 31, 31);
      }
    }
  }
}
</style>