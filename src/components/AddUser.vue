<template>
  <div class="container">
    <div class="input-box">
      <input type="text" v-model="input" placeholder="imię (pseudonim)" v-on:keyup.enter="addClicked">
    </div>
    <div class="button-box">
      <font-awesome-icon :icon="['fas', 'plus-circle']" class="add" @click="addClicked"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddUser',
  data() {
    return {
      input: ''
    }
  },
  methods: {
    addClicked() {
      if(this.input.trim() != '') {
        this.$emit('added', this.input);
        this.input = '';
      } else {
        alert('Okno jest puste');
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  .container {
    width: 80%;
    height: 3rem;
    background-color: #35495e;
    border-radius: 1rem;
    overflow: hidden;
    display: flex;
    flex-direction: row;
    
    .input-box {
      flex: 5;
      display: flex;

      input {
        width: 100%;
        outline: none;
        background-color: #2b3c4e;
        border: none;
        color: white;
        padding: 1rem;
        font-size: 1rem;
      }
    }
    .button-box {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;

      .add {
        color: #42b883;
        font-size: 2rem;
        transition: 0.1s;

        &:hover {
          color: #338d64;
          cursor: pointer;
        }
      }
    }
  }
</style>