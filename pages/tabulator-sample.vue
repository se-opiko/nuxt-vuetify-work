<script setup>
import { ref, reactive, onMounted } from "vue";
import { TabulatorFull as Tabulator } from "tabulator-tables"; //import Tabulator library

const table = ref(null); //reference to your table element
const tabulator = ref(null); //variable to hold your table
const tableData = reactive([
  {
    id: 1,
    name: "Billy Bob",
    age: "12",
    gender: "male",
    col: "red",
  },
  {
    id: 2,
    name: "Mary May",
    age: "1",
    gender: "female",
    col: "blue",
  },
  {
    id: 3,
    name: "Christine Lobowski",
    age: "42",
    col: "green",
  },
]); //data for table to display

onMounted(() => {
  //instantiate Tabulator when element is mounted
  tabulator.value = new Tabulator(table.value, {
    data: tableData, //link data to table
    reactiveData: true, //enable data reactivity
    columns: [
      { title: "Name", field: "name", width: 150, editor: "input" },
      { title: "Age", field: "age", hozAlign: "left", formatter: "progress" },
      { title: "Favourite Color", field: "col" },
      {
        title: "Rating",
        field: "rating",
        hozAlign: "center",
        formatter: "star",
      },
    ], //define table columns
  });
});
</script>

<template>
  <div ref="table"></div>
</template>
