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

    for (let i = 0; i < 5; i++) {
      data.push(data[0]);
    }

    const grid = new Grid({
      columns: columns,
      data: data,
      search: {
        enabled: true,
      },
      className: {
        table: "grid__table",
        thead: "grid__thead",
        th: "grid__th",
        td: "grid__td",
        search: "grid__search",
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

.gridjs-th {
  padding: 0.5rem 1rem;
}

.gridjs-td {
  padding: 0.5rem 1rem;
}

.gridjs-tr {
  border-top: 1px solid lightgray;
  border-bottom: 1px solid lightgray;
}
</style>
