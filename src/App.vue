<template>
  <div id="app">
    <h1>Monty Hall Problem</h1>
    <div class="form">
      <div class="questions" v-if="!started">
        <label for="doorsAmount">How many doors?</label>
        <input type="text" id="doorsAmount" size="3" v-model.number="doorsAmount">
      </div>
      <div class="questions" v-if="!started">
        <label for="doorWithGift">Which door has the gift?</label>
        <input type="text" id="doorWithGift" size="3" v-model.number="doorWithGift">
      </div>
      <button v-if="!started" @click="started = true">Start</button>
      <button v-if="!started" @click="started = false">Restart</button>
    </div>
    <div class="description" v-if="started">
      <h3>Goal: Find the gift behind the door. At least 2 people are required to play.</h3>
      <h3>Ask to your friend to choose one of the doors, but you don't open it right away. Just click 1 time to select the door.</h3>
      <h3>Open one door of the other doors, but not the chosen one. 2 clicks to open the door.</h3>
      <h3>If this door is empty, ask your friend if he/she wants to switch the chosen port or not.</h3>
      <h3>Do this until you find the gift.</h3>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in doorsAmount" :key="i">
        <TheDoor :hasGift="i === doorWithGift" :number="i" />        
      </div>
    </div>
  </div>
</template>

<script>
import TheDoor from "./components/TheDoor.vue";

export default {
  name: 'App',
  components: { TheDoor },
  data: function() {
    return {
      started: false,
      doorAmount: 3,
      selectedDoor: null,
    }
  }
}
</script>

<style>

* {
  box-sizing: border-box;
  font-family: "Montserrat", sans-serif;
}

body {
  color: rgb(77, 0, 0);
  background: rgb(225, 225, 225);
}

#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#app h1 {
  border-bottom: 5px solid rgb(113, 0, 0);
  padding: 40px 0px;
  margin-bottom: 60px;
}

.description {
  position: absolute;
  top: 160px;
  padding-bottom: 100px;
}

.description h3 {
  font-size: 16px;
  text-align: center;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}

.form label {
  margin-bottom: 10px;
  font-size: 1.3rem;
  font-weight: bold;
}

.form input {
  margin-bottom: 10px;
  font-size: 1.2rem;
  border-radius: 5px;
}

.form button {
  margin: 15px;
  border-radius: 8px;
  font-size: 1.5rem;
}

.questions {
  padding: 10px;
}

.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  padding-top: 130px;
}

label {
  padding: 20px;
}

</style>
