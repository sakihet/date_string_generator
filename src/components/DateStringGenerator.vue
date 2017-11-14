<template lang="pug">
  .container
    h1 {{ msg }}
    .cell
      .addon
        span.addon-item prefix
        input.addon-field(type="text" v-model="prefix")
    .cell
      .addon
        span.addon-item locale
        input.addon-field(type="text" v-model="locale")
    .cell
      .addon
        span.addon-item start date
        input.addon-field(type="date" v-model="startDate")
    .cell
      .addon
        span.addon-item days
        input.addon-field(type="number" v-model="days")
    .cell
      .addon
        span.addon-item format
        input.addon-field(type="text" v-model="dateFormat")
    .cell
      textarea(v-model="textarea" rows="10" style="font-family: monospace;" readonly="true")
    .cell
      button(@click="copy") copy to clipboard
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
      startDate: moment().format('YYYY-MM-DD'),
      days: 7,
      dateFormat: 'YYMMDDddd'
    }
  },
  computed: {
    textarea () {
      moment.locale(this.locale)
      var str = ''
      for (var i = 0; i < this.days; i++) {
        str += this.prefix + moment(this.startDate).add(i, 'day').format(this.dateFormat)
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
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.cell {
  flex: 1;
}
.addon {
  display: flex;
}
.addon-item {
  text-align: right;
  width: 80px;
  padding-right: 5px;
}
.addon-field {
  flex: 1;
}
textarea {
  background-color: #f7f7f7;
}
</style>
