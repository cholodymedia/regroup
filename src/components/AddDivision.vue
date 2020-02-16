<template>
  <div class="container">
    <div class="box">
      <div class="number">
        <input type="number" v-model.number="division" @change="divisionChange">
      </div>
      <div class="controls">
        <div class="up">
          <font-awesome-icon :icon="['fas', 'arrow-up']" class="arrow" @click="numberUp"/>
        </div>
        <div class="down">
          <font-awesome-icon :icon="['fas', 'arrow-down']" class="arrow" @click="numberDown"/>
        </div>
      </div>
    </div>
    <div class="info">
      <span v-if="podzial && !error">Podział będzie całkowity</span>
      <span v-if="!podzial && !error">Podział nie będzie całkowity</span>
      <span v-if="error" class="error">Nie ma tylu ludzi!!!</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddDivision',
  data() {
    return {
      division: 1,
    }
  },
  props: {
    people: Number,
    divis: Number
  },
  methods: {
    numberUp() {
      this.division++;
      this.divisionChange();
    },
    numberDown() {
      if(this.division > 1) {
        this.division--;
        this.divisionChange();
      }
    },
    divisionChange() {
      this.$emit('change', this.division);
    }
  },
  computed: {
    podzial() {
      if(this.people %this.division == 0) {
        return true;
      } else {
        return false;
      }
    },
    error() {
      if(this.people < this.division) {
        return true;
      } else {
        return false;
      }
    }
  },
  created() {
    if(this.divis != 2) {
      this.division = this.divis;
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center
}
.box {
  width: 10rem;
  height: 7rem;
  background-color: #2b3c4e;
  border-radius: 1rem;
  display: flex;
  flex-direction: row;
  overflow: hidden;

  .number {
    width: 7rem;
    height: 100%;
    display: flex;
    input::-webkit-outer-spin-button,
    input::-webkit-inner-spin-button {
      -webkit-appearance: none;
      margin: 0;
    } 

    input {
      width: 100%;
      height: 100%;
      border: none;
      background: none;
      outline: none;
      text-align: center;
      color: white;
      font-size: 2rem;
      padding-left: 1rem;
      padding-right: 1rem;
    }
  }

  .controls {
    flex: 1;
    height: 100%;
    display: flex;
    flex-direction: column;

    .up {
      flex: 1;
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      font-size: 1.5rem;
    }
    .down {
      flex: 1;
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      font-size: 1.5rem;
    }
    .arrow {
      transition: 0.2s;
      &:hover {
        color: rgb(211, 211, 211);
        cursor: pointer;
      }
    }
  }
}
.info {
  margin-top: 2rem;
  width: 20rem;
  height: 3rem;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-size: 1.2rem;

  .error {
    color: #b84a42;
    font-weight: bold;
  }
}
</style>