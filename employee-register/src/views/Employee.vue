<template>
  <div>
    <TableEmployee  title="List of Employees"/>
    <EmployersList title="List of Employers"/>
  </div>
</template>

<script>

import TableEmployee from "@/components/TableEmployee.vue";
import EmployersList from "@/components/EmployersList.vue";


export default {
  name: "Employee",
  components: {
    TableEmployee,
    EmployersList,
  },
};
</script>

