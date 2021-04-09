<template>
    <div class="mt-4">
        <h1>{{ title }}</h1>
        <div class="table-responsive">
            <table class="table table-success table-responsive">
                <thead class="table-dark">
                    <tr>
                        <th scope="col">Email</th>
                        <th scope="col">Employer</th>
                        <th scope="col">N° Phone</th>
                        <th scope="col">CNSS</th>
                        <th scope="col">Address</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-bind:key="employer.id" v-for="employer in employers">
                        <td>{{employer.email}}</td>
                        <td>{{employer.employer}}</td>
                        <td>{{employer.phone}}</td>
                        <td>{{employer.cnss}}</td>
                        <td>{{employer.address}}</td>
                    </tr>
                </tbody>
            </table> 
        </div>
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: "EmployersList",
    props: {
        title: String,
    },
    data(){
        return {
            employers:[]
        }
    },
    methods: {
        getEmployers() {
            axios.get('http://localhost:3000/employers')
                 .then(res => this.employers = res.data)
                 .catch(err => console.log(err))
        }
    },
    created(){
        this.getEmployers();
    }
};
</script>
