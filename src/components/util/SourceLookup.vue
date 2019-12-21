<template>
  <div>
    <b-input-group>
      <b-form-input placeholder="Search sources" v-model="sourceName"></b-form-input>
      <b-input-group-append>
        <b-button variant="outline-info" @click="lookup">🔍</b-button>
      </b-input-group-append>
    </b-input-group>
    <b-input-group>
      <b-form-input placeholder="ra" v-model="ra"></b-form-input>
      <b-form-input placeholder="dec" v-model="dec"></b-form-input>
    </b-input-group>
    <span class="text-danger" v-if="error">{{ error }}</span>
  </div>
</template>
<script>
export default {
  name: 'SourceLookup',
  data: () => {
    return {
      sourceName: '',
      ra: '',
      dec: '',
      error: null
    }
  },
  methods: {
    lookup: function() {
      fetch('https://simbad2k.lco.global/' + this.sourceName).then(response => {
        response.json().then(data => {
          if(data.error){
            this.error = data.error
          }else{
            this.ra = data.ra.replace(/ /g, ':')
            this.dec = data.dec.replace(/ /g, ':')
          }
        })
      }).catch(e => {
        this.error = 'There was a problem with your request ' + e
      })
    }
  }
}
</script>

