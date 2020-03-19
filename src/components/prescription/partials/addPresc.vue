<template>
  <div>
    <q-card bordered flat class="link flex flex-center text-primary" @click="alert = true" style="min-width: 150px">
      <q-card-section>
        <q-icon name="add" size="xl"/>
      </q-card-section>
    </q-card>
    <q-dialog v-model="alert">
      <Dosage @dosage="$emit('dosage', $event)"/>
    </q-dialog>
  </div>
</template>

<script>
import Dosage from './dosage'
export default {
  // name: 'ComponentName',
  components:{
    Dosage
  },
  data () {
    return {
      alert: false,
      value: false,
      options: [
        'Tablets', 'Injection', 'Syrup'
      ],
      form:{
        name: '',
        duration: '',
        type: 'Tablets',
        morning: '',
        afternoon: '',
        night: '',
        hourly:{dosage: '', hours: ''},
      }
    }
  },

  methods: {
    usageFnc(){
      this.$emit('dosage', this.form)
      this.form = []
      this.alert = false
    }
  },

  computed: {
    route(){return this.$route.name}
  },
}
</script>
