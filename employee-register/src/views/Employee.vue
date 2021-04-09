<template>
  <div class="emloyee">
    <TableEmployee  title="List of Employees"/>
  </div>
</template>

<script>

import TableEmployee from "@/components/TableEmployee.vue";

export default {
  name: "Employee",
  components: {
    TableEmployee
  },
};
</script>

