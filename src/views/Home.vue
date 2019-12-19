<template>
  <div class="row">
    <div class="col-sm-3">
      <FilterForm></FilterForm>
    </div>
    <div class="col">
      <HelloWorld msg="Welcome to Your Vue.js App"/>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import FilterForm from '@/components/FilterForm.vue'

export default {
  name: 'home',
  components: {
    HelloWorld,
    FilterForm
  }
}
</script>
