<template>
  <div id="app">
   <div class="title-box">Re-Group</div>
   <div class="main-box">
     <div class="top">
       <span v-if="stages.stage_1">Dodaj ludzi</span>
       <span v-if="stages.stage_2">Podaj ilość ludzi w zespole</span>
       <span v-if="stages.stage_3">Dodaj ludzi</span>
     </div>
     <div class="body">
       <AddUser @added='addUser' v-if="stages.stage_1"/>
        <div class="display-users" v-if="stages.stage_1">
          <DisplayUser class="single-user" v-for="(user, index) in people" :key="index" :name="user" :id="index" @delete="userDelete"/>
        </div>
     </div>
     <div class="bottom">
       <div class="left">
         <span v-if="stages.stage_1">Dodano: {{people.length}}</span>
       </div>
       <div class="right">
         <div class="next" @click="nextStage">Dalej</div>
       </div>
     </div>
   </div>
  </div>
</template>

<script>
import AddUser from '@/components/AddUser'
import DisplayUser from '@/components/DisplayUser'

export default {
  name: 'App',
  data() {
    return {
      people: [],
      division: null,
      stages: {
        stage_1: true,
        stage_2: false,
        stage_3: false
      }
    }
  },
  components: {
    AddUser,
    DisplayUser
  },
  methods: {
    addUser(name) {
      this.people.push(name);
    },
    userDelete(id) {
      this.people.splice(id, 1);
      console.log(id);
    },
    nextStage() {
      if(this.stages.stage_1) {
        if(this.people.length != 0) {
          this.stages.stage_1 = false;
          this.stages.stage_2 = true;
        } else {
          alert('Dodaj ludzi!!!');
        }
      }
    }
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,500&display=swap');
@import url('https://fonts.googleapis.com/css?family=Sriracha&display=swap');

* {
  margin: 0;
  padding: 0;
  font-family: Montserrat;
}

body {
  overflow-x: hidden;
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100vw;
  min-height: 100vh;
  background-color: #42b883c0;

  .title-box {
    margin-top: 1rem;
    width: 20rem;
    height: 7rem;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 3rem;
    color: #35495e;
    font-family: Sriracha;
  }

  .main-box {
    margin-top: 1rem;
    min-height: 30rem;
    width: 30rem;
    background-color: #35495ee7;
    border-radius: 1rem;
    display: flex;
    flex-direction: column;
    margin-bottom: 4rem;

    .top {
      width: 100%;
      height: 5rem;
      display: flex;
      justify-content: center;
      align-items: center;
      color: whitesmoke;
      font-size: 1.3rem;
      font-weight: 500;
    }

    .body {
      width: 100%;
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;

      .display-users {
        width: 100%;
        height: auto;
        flex: 1;
        display: grid;
        grid-template-columns: 1fr 1fr;
        padding-top: 1.5rem;
        padding-bottom: 0.5rem;
        grid-row-gap: 1rem;

        .single-user {
          justify-self: center;
        }
      }
    }

    .bottom {
      width: 100%;
      height: 5rem;
      display: flex;
      flex-direction: row;
      .left {
        flex: 1;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        color: whitesmoke;
        font-size: 1.1rem;
        font-weight: 500;
        padding-left: 1.5rem;
      }
      .right {
        flex: 1;
        display: flex;
        align-items: center;
        justify-content: flex-end;

        .next {
        width: 6rem;
        height: 2.5rem;
        margin-right: 1.5rem;
        background-color: #42b883;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 2rem;
        color: whitesmoke;
        font-weight: 500;
        font-size: 1rem;
        transition: 0.2s;
        &:hover {
          background-color: #359c6e;
          cursor: pointer;
        }
      }
      }
    }
  }
}
</style>
