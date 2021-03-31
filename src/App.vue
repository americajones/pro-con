<template>
<div class="header">
<p>what's it about this time?</p>
<input class="topInput" v-model="inputName">
</div>

<h2>{{ inputName }} pros and cons</h2>
  <Procon></Procon>
</template>

<script>
import Procon from './components/Procon.vue'

export default {
  name: 'App',
  components: {
    Procon
  },
  data() {
    return {
      inputName: ""
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #aaaaaa;
  margin-top: 1rem;
}
body {
  background-color: rgb(43, 43, 43);
}
.header {
  display: flex;
  flex-direction: row;
  margin: auto;
  width: 400px;
  flex: none;
  color: #888888;

}
.topInput {
  height: 1rem;
  align-self: center;
  margin: 1rem;
  border: none;
  background-color: rgb(200, 207, 207);
}
h2{
  font-size: 2em;
}
</style>
