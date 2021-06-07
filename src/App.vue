<template>
  <div id="app">
    <div id="grid" />
  </div>
</template>

<script>
import { Grid, html } from "gridjs";

export default {
  mounted: () => {
    const columns = [
      {
        name: "Picture",
        formatter: (cell) =>
          html(`<img src="${cell}" style="width: 200px;" />`),
      },
      {
        name: "Name",
      },
      {
        name: "Email",
      },
      {
        name: "Phone Number",
      },
    ];

    const data = [
      {
        picture: "./img/owl.jpg",
        name: "John",
        email: " john@john.com",
        phoneNumber: "000-0000-0000",
      },
    ];

    for (let i = 0; i < 3; i++) {
      data.push(data[0]);
    }

    const grid = new Grid({
      columns: columns,
      data: data,
      search: {
        enabled: true,
      },
      style: {
        table: {
          width: "600px",
        },
      },
    });

    grid.render(document.getElementById("grid"));
  },
};
</script>

<style>
.gridjs-container {
  overflow-x: auto;
}

.gridjs-table {
  max-width: 100%;
  border-collapse: collapse; /* セル同士の境界をなくす */
  text-align: center;
  overflow: auto;
  border: none;
}

th.gridjs-th {
  border: 1px solid lightgray;
  width: 150px;
  padding: 1rem;
  text-align: center;
}

td.gridjs-td {
  border: 1px solid lightgray;
  height: 100px;
  text-align: right;
  padding-right: 1rem;
}
td.gridjs-td:first-child {
  text-align: center;
  padding-right: 0;
}
</style>
