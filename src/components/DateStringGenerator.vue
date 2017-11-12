<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <label>prefix:
      <input type="text" v-model="prefix">
    </label>
    <br>
    <label>locale:
      <input type="text" v-model="locale">
    </label>
    <br>
    <label>days:
      <input type="number" v-model="days">
    </label>
    <br>
    <textarea v-model="textarea" rows="20" style="font-family: monospace;"></textarea>
    <br>
    <button @click="copy">copy to clipboard</button>
  </div>
</template>

<script>
import mcopy from 'modern-copy'
const moment = require('moment')

export default {
  name: 'DateStringGenerator',
  data () {
    return {
      msg: 'date string generator',
      prefix: '# ',
      text: 'test',
      locale: 'en',
      days: 7
    }
  },
  computed: {
    textarea () {
      moment.locale(this.locale)
      var str = ''
      for (var i = 0; i < this.days; i++) {
        str += this.prefix + moment().add(i, 'day').format('YYMMDDddd')
        str += '\n'
      }
      return str
    }
  },
  methods: {
    copy () {
      mcopy(this.textarea)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
