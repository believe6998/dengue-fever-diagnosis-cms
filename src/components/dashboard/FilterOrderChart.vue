<template>
  <div>
    <div class="q-col-gutter-lg row justify-end">
      <q-select outlined
                v-model="filter.year"
                :options="yearOptions"
                label="Lọc theo năm"
                class="col-6 col-sm-4 col-md-2"
                dense
                clearable
                @clear="clearFilter"
                @input="doLoadStatistical"
      />
    </div>
    <div class="text-h5 text-center">Biểu đồ Doanh thu / Số lượng đơn hàng theo từng tháng trong năm</div>
  </div>
</template>

<script>
import { Constants } from 'src/utils/const'
import { mapActions } from 'vuex'

export default {
  name: 'FilterOrderChart',
  data () {
    return {
      filter: {}
    }
  },
  mounted () {
    this.filter = {
      ...{ year: Constants.YearBegin }
    }
  },
  computed: {
    yearOptions () {
      const currentYear = new Date().getFullYear()
      const yearOptions = []
      for (let i = Constants.YearBegin; i <= currentYear; i++) {
        yearOptions.push(i)
      }
      return yearOptions
    }
  },
  methods: {
    ...mapActions({
      loadStatistical: 'order/loadStatistical'
    }),
    clearFilter () {
      this.filter = {}
      this.doLoadStatistical()
    },
    async doLoadStatistical () {
      await this.loadStatistical(this.filter)
      this.$emit('renderChart')
    }
  }
}
</script>

<style scoped>

</style>
