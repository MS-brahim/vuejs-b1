<template>
    <div>
        <h1>{{ title }}</h1>
        <div class="table-responsive">
            <table class="table table-success table-responsive">
                <thead class="table-dark">
                    <tr>
                        <th scope="col">Photo</th>
                        <th scope="col">First name</th>
                        <th scope="col">Last name</th>
                        <th scope="col">N° Phone</th>
                        <th scope="col">CIN</th>
                        <th scope="col">N° Passport</th>
                        <th scope="col">Address</th>
                        <th scope="col">City</th>
                        <th scope="col">Country</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-bind:key="employee.id" v-for="employee in employees">
                        <td><img src="../assets/logo.png" width="40px" alt=""></td>
                        <td>{{employee.firstName}}</td>
                        <td>{{employee.lastName}}</td>
                        <td>{{employee.phone}}</td>
                        <td>{{employee.cin}}</td>
                        <td>{{employee.passport}}</td>
                        <td>{{employee.address}}</td>
                        <td>{{employee.city}}</td>
                        <td>{{employee.country}}</td>
                    </tr>
                </tbody>
            </table> 
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "TableEmployee",
    props: {
        title: String,
    },
    data(){
        return {
            employees:[]
        }
    },
    methods: {
        getEmployees() {
            axios.get('http://localhost:3000/employees')
                 .then(res => this.employees = res.data)
                 .catch(err => console.log(err))
        }
    },
    created(){
        this.getEmployees();
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
