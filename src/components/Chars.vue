<template>
  <center>
    <button @click="tableVisible = !tableVisible">Toggle Chars Table</button>

    <table v-show="tableVisible" class="chars-table">
      <thead>
        <tr>
          <th>Character</th>
          <th>Count</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(count, char) in dictionary" :key="char">
          <td class="center-cell">{{ char }}</td>
          <td>
            <input type="number" class="center-cell" v-model.number="dictionary[char]" min="0" />
          </td>
        </tr>
      </tbody>
    </table>
  </center>
</template>

<script>
  export default {
    name: "Chars",
    data: () => ({
      tableVisible: false
    }),
    props: {
      dictionary: Object
    }
  };
</script>

<style scoped>
  table,
  th,
  td {
    border: 1px solid black;
  }

  .center-cell {
    text-align: center;
  }
</style>
