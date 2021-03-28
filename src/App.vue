<template>
  <div id="app">
    <textarea rows="4" cols="100" v-model="feedbackTextArea"/>
    <Speech2Text @speechend="speechEnd" />
  </div>
</template>

<script>
import Speech2Text from './components/STT.vue'

export default {
  name: 'App',
  components: {
    Speech2Text
  },
  data() {
    return {
      feedbackTextArea: '',
    }
  },
  methods: {
    speechEnd({text}) {

      if (text) {
        this.feedbackTextArea += text + '. '
      }

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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
