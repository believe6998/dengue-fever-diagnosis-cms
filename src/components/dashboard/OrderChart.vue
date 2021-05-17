<template>
  <div>
    <FilterOrderChart class="q-mb-md" @renderChart="doRenderChart"/>
    <BarChart ref="barChart" :statistical="statistical"/>
  </div>
</template>

<script>
import BarChart from '../common/chart/BarChart'
import FilterOrderChart from './FilterOrderChart'
import { mapActions, mapState } from 'vuex'

export default {
  name: 'OrderChart',
  components: {
    BarChart,
    FilterOrderChart
  },
  async mounted () {
    await this.loadStatistical()
  },
  computed: {
    ...mapState('order', [
      'statistical',
      'isLoading',
      'error'
    ])
  },
  methods: {
    ...mapActions({
      loadStatistical: 'order/loadStatistical'
    }),
    doRenderChart () {
      this.$refs.barChart.doRenderChart()
    }
  }
}
</script>

<style scoped>

</style>
