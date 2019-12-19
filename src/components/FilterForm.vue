<template>
  <b-form>
    <VueCtkDateTimePicker :range="true" v-model="params.range"></VueCtkDateTimePicker>
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
import VueCtkDateTimePicker from 'vue-ctk-date-time-picker';
import moment from 'moment';
import 'vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css';
export default {
  name: 'FilterForm',
  components: {VueCtkDateTimePicker},
  data: function(){
    return {
      params: {
        range: {
          start: moment().format('YYYY-MM-DD'),
          end: moment().format('YYYY-MM-DD'),
        },
        proposal: null,
        basename: null,
      }
    }
  }
}
</script>
