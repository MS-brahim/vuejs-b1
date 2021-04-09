<template>
  <div>
      <h1>{{ title }}</h1>
{{email}}
      <form class="card container p-4">
      <div class="row">
        <div class="col-sm-6 mt-2">
          <input v-model="email" type="text" class="form-control" placeholder="email...">
        </div>
        <div class="col-sm-6 mt-2">
          <input v-model="employer" type="text" class="form-control" placeholder="employer...">
        </div>
      </div>
      <div class="row">
        <div class="col-sm-4 mt-2">
          <input v-model="phone" type="text" class="form-control" placeholder="phone">
        </div>
        <div class="col-sm-4 mt-2">
          <input v-model="cnss" type="text" class="form-control" placeholder="cnss">
        </div>
      </div>
      <div class="row">
        <div class="col-sm-12 mt-2">
          <textarea v-model="address" type="text" class="form-control" placeholder="address..."></textarea>
        </div>
      </div>
      <input @click="saveEmployer()" type="button" value="Save" class="btn btn-success mt-4 col-sm-3">
    </form>

  </div>
</template>

<script>
import axios from 'axios';
export default {
props: {
    title: String,
  },
  data(){
    return {
      email:'',
      employers:[]
    }
  },
  methods:{
    saveEmployer() {
      // e.preventdefault();
      let newEmployer = {
        email     : this.fname,
        employer  : this.employers,
        phone     : this.phone,
        cnss      : this.cnss,
        address   : this.address,

      }
      axios.post('http://localhost:3000/employers',newEmployer)
           .then(res => console.log(res.data))
    }
  }
}
</script>

<style>

</style>