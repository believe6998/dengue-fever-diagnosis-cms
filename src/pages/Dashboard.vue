<template>
  <q-page class="q-py-sm q-pl-sm">
    <q-card>
      <q-card-section>
        <OrderChart/>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
import OrderChart from '../components/dashboard/OrderChart'

export default {
  name: 'Dashboard',
  components: {
    OrderChart
  },
  data () {
    return {}
  }
}
</script>
