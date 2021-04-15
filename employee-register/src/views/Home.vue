<template>
  <div class="row">
    <div class="col-sm-6">
      <FormEmployee title="Create New Employee"/>
    </div>
    <div class="col-sm-6">
      <FormEmployer title="New Employer"/>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import FormEmployee from "@/components/FormEmployee.vue";
import FormEmployer from "@/components/FormEmployer.vue";

export default {
  name: "Home",
  components: {
    FormEmployee,
    FormEmployer,
  },
};
</script>
