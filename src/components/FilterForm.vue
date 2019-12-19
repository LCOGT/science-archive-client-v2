<template>
  <b-form>
    <DateTimePicker @datepicked="datePicked"></DateTimePicker>
    <b-form-group
      id="input-group-basename"
      label="Basename"
      label-for="input-basename"
    >
      <b-form-input
        id="input-basename"
        v-model="params.basename"
      ></b-form-input>
    </b-form-group>
      {{ params }}
    <b-button type="reset">Reset</b-button>
  </b-form>
</template>
<script>
import DateTimePicker from '@/components/util/DateTimePicker.vue'
export default {
  name: 'FilterForm',
  components: {DateTimePicker},
  data: function(){
    return {
      params: {
        range: {
          start: null,
          end: null,
        },
        proposal: null,
        basename: null,
      }
    }
  },
  methods: {
    datePicked: function(v){
      this.params.range.start = v.start
      this.params.range.end = v.end
    }
  }
}
</script>
