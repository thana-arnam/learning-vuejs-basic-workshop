<template>
  <div>
    <ul>
      <Person
        v-for="(item, index) in employees"
        v-bind:key="index"
        v-bind:name="item.name"
        v-bind:salary="item.salary"
        v-bind:department="item.department"
        v-bind:gender="item.gender"
        v-bind:skill="item.skill"
      />
      <!-- <Person
        v-for="(item, index) in employees"
        v-bind:key="index"
        v-bind:id="item.id"
        v-bind:name="item.name"
        v-bind:salary="item.salary"
        v-bind:department="item.department"
        v-bind:isVisable="item.isVisable"
        @show="toggleVisable"
        @delete="removeEmployee"
      /> -->
    </ul>
  </div>
</template>

<script>
import Person from "./Person.vue";

export default {
  name: "ListData",
  components: {
    Person,
  },
  props: ["employees"]
  //   data() {
  //     return {
  //       employees: [
  //         {id: 1, name: "Charlotte Austin", salary: 10000, department: "Graphic", isVisable: false},
  //         {id: 2, name: "KimmTaeyeon", salary: 10000, department: "Programmer", isVisable: false},
  //         {id: 3, name: "Tiffany Young", salary: 10000, department: "Manager", isVisable: false},
  //         {id: 4, name: "Engfah Waraha", salary: 10000, department: "Product Owner", isVisable: false},
  //         {id: 5, name: "Jessica Jong", department: "Tester", isVisable: false}
  //       ]
  //     }
  //   },
  //   methods: {
  //     toggleVisable(employeeId) {
  //         const emp = this.employees.find(emp => emp.id === employeeId);
  //         emp.isVisable = !emp.isVisable;
  //     },
  //     removeEmployee(employeeId) {
  //         this.employees = this.employees.filter(emp => emp.id !== employeeId);
  //     }
  //   }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 1rem 0;
  padding: 0;
}
</style>
