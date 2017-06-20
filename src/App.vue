<template>
  <div id="app" class="is-parent" style="width: 30rem; margin:auto; margin-top: 2rem;"> 
    <div class="box is-child">
      <p>Date: {{date}}</p>
      <cleave v-model="date" 
        placeholder="Date" 
        :options="{ date: true, datePattern: [ 'm', 'd', 'Y'] }">
      </cleave>
    </div>

    <div class="box is-child">
      <p>Phone Num: {{phone.value}}</p>
      <cleave
         class="input"
         v-model="phone.value"
         @rawValueChanged="onRawValueChanged"
         placeholder="Enter phone number"
         :options="{ blocks: [0, 3, 3, 4], numericOnly: true, delimiters: ['(', ') ', '-'], maxLength: 14 }">
      </cleave>
    </div>
  </div>
</template>

<script>
import Cleave from 'vue-cleave'

export default {
  name: 'app',
  data () {
    return {
      date: '01-01-2018',
      phone: {
        value: '',
        rawValue: ''
      }
    }
  },
  methods: {
    onRawValueChanged (newVal) {
      this.phone.rawValue = newVal
    }
  },
  components: {
    Cleave
  }
}
</script>

<style lang="scss">
@import '~bulma';

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
