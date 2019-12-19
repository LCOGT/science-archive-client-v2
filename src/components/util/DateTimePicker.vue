<template>
  <VueCtkDateTimePicker
    :range="true"
    v-model="range"
    :custom-shortcuts="datepickerShortcuts"
    @input="emitValue"
  ></VueCtkDateTimePicker>
</template>
<script>
import VueCtkDateTimePicker from 'vue-ctk-date-time-picker'
import moment from 'moment'
import 'vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css'
export default {
  name: 'DateTimePicker',
  components: {VueCtkDateTimePicker},
  data: function(){
    return {
      range: {
        start: null,
        end: null
      },
      currentSemester: {
        start: null,
        end: null
      },
      lastSemester: {
        start: null,
        end: null
      },
      datepickerShortcuts: [
        {
          key: 'currentSemester',
          label: 'This Semester',
          value: () => {
            return {start: this.currentSemester.start, end: this.currentSemester.end}
          }
        },
        {
          key: 'lastSemester',
          label: 'Last Semester',
          value: () => {
            return {start: this.lastSemester.start, end: this.lastSemester.end}
          }
        },
        {
          key: 'alltime',
          label: 'All Time',
          value: () => {
            return {start: moment('1988-07-17', 'YYYY-MM-DD'), end: moment('2048-01-01', 'YYYY-MM-DD')}
          }
        },
        {key: 'today', label: 'Today', value: 'day'},
        {key: 'yesterday', label: 'Yesterday', value: '-day'},
        {key: 'last7days', label: 'Last 7 days', value: 7},
        {key: 'last30days', label: 'Last 30 days', value: 30},
      ]
    }
  },
  methods: {
    fetchSemesters: function(){
      const now = moment.utc().format('YYYY-MM-DD HH:mm')
      fetch('https://observe.lco.global/api/semesters/?start_lte=' + now).then(response => {
        response.json().then(data => {
          this.currentSemester.start = moment.utc(data['results'][0].start)
          this.currentSemester.end = moment.utc(data['results'][0].end)
          this.lastSemester.start = moment.utc(data['results'][1].start)
          this.lastSemester.end = moment.utc(data['results'][1].end)
          if(!this.range.start){
            this.range.start = this.currentSemester.start.format('YYYY-MM-DD HH:mm')
          }
          if(!this.range.end){
            this.range.end = this.currentSemester.end.format('YYYY-MM-DD HH:mm')
          }

        })
      }).catch(e => {
        console.log(e)
      })
    },
    emitValue: function(v){
      this.$emit('datepicked', v)
    }
  },
  mounted: function(){
    this.fetchSemesters()
  }
}
</script>
