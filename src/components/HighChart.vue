<template>
  <div style="margin: 0 auto;width:100%;height:100%;">

  </div>
</template>

<script>
var Highcharts = require('highcharts')
require('highcharts/modules/boost')(Highcharts)
// require('highcharts/modules/exporting')(Highcharts)

export default {
  props: {
    options: {
      type: Object,
      default: () => ({})
    }
  },
  data () {
    return {
      chart: null
    }
  },
  watch: {
    options: function (value) {
      this.chart.update(value, true)
      return value
    }
  },
  mounted () {
    this.chart = Highcharts.chart(this.$el, this.options)
  },
  beforeDestroy () {
    this.chart.destroy()
  }
}
</script>