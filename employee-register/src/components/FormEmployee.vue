<template>
  <div>
    <h1>{{ title }}</h1>
    {{image}}
    <form class="card container p-4" enctype="multipart/form-data">
      <div class="row">
        <div class="col-sm-6 mt-2">
          <input v-model="fname" type="text" class="form-control" placeholder="first name">
        </div>
        <div class="col-sm-6 mt-2">
          <input v-model="lname" type="text" class="form-control" placeholder="first name">
        </div>
      </div>
      <div class="row">
        <div class="col-sm-4 mt-2">
          <input v-model="phone" type="text" class="form-control" placeholder="phone number">
        </div>
        <div class="col-sm-4 mt-2">
          <input v-model="cin" type="text" class="form-control" placeholder="CIN">
        </div>
        <div class="col-sm-4 mt-2">
          <input v-model="passport" type="text" class="form-control" placeholder="N°Passport">
        </div>
      </div>
      <div class="row">
        <div class="col-sm-12 mt-2">
          <textarea v-model="address" type="text" class="form-control" placeholder="address"></textarea>
        </div>
        <div class="col-sm-4 mt-2">
          <input v-model="city" type="text" class="form-control" placeholder="city">
        </div>
        <div class="col-sm-4 mt-2">
          <input v-model="country" type="text" class="form-control" placeholder="country">
        </div>
        <div class="col-sm-4 mt-2">
          <input @change="fileSelected" ref="file" type="file" class="form-control">
        </div>
      </div>
      <input @click="saveEmployee()" id="img" type="button" value="Save" class="btn btn-success mt-4 col-sm-3">
    </form>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "FormEmployee",
  props: {
    title: String,
  },
  data(){
    return {
      employees:[],
      file:'',
    }
  },
  methods:{
    fileSelected(event){
      console.log(event.target.files[0].name);
      this.file = this.$refs.file.files[0];
      // this.file = event.target.files[0]
    },
    saveEmployee() {
      
      let fd = new FormData();
      fd.append('file', this.file);

      let newEmployee = {
        firstName : this.fname,
        lastName  : this.lname,
        phone     : this.phone,
        cin       : this.cin,
        passport  : this.passport,
        address   : this.address,
        city      : this.city,
        country   : this.country,
        image     : this.$refs.file.files[0].name,

      }
      console.log(fd);
      axios.post('http://localhost:3000/employees',newEmployee)
           .then(res => console.log(res.data))
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
