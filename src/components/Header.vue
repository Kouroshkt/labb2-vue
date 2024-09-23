<template>
  <h2>Träningsschema för 4 dagar i veckan</h2>
  <table>
    <tbody>
    <tr>
      <th>Dag</th>
      <th>Träningspass</th>
    </tr>

    <tr>
      <td>Måndag</td>
      <td>Pass 1</td>
    </tr>

    <tr>
      <td>Tisdag</td>
      <td>Vila/annan träning</td>
    </tr>

    <tr>
      <td>Onsdag</td>
      <td>Pass 2</td>
    </tr>

    <tr>
      <td>Torsdag</td>
      <td>Vila/annan träning</td>
    </tr>

    <tr>
      <td>Fredag</td>
      <td>Pass 3</td>
    </tr>

    <tr>
      <td>Lördag</td>
      <td>Pass 4</td>
    </tr>

    <tr>
      <td>Söndag</td>
      <td>Vila/annan träning</td>
    </tr>

    </tbody>
  </table>
</template>

<style scoped>
h2 {
  color: #bb8d55;
  text-align: center;
  font-size: 28px;
  font-family: Tahoma, Arial, sans-serif;
}
table {
  width: 100%;
  border-collapse: collapse;
  margin: 20px 0;
  font-size: 18px;
  text-align: left;
}

th, td {
  padding: 12px 15px;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #c6c1db;
  font-weight: bold;
  text-transform: uppercase;
}

tr:nth-child(even) {
  background-color: #f9f9f9;
}

tr:hover {
  background-color: #f1f1f1;
}

tbody tr:last-child td {
  border-bottom: none;
}
@media (min-width: 800px) and (max-width: 1100px) {
  h2{
    font-size: 35px;
  }
  table{
    font-size: 22px;
  }
}
@media (max-width: 799px) {
  table{
    font-size: 15px;
  }
  h2{
    font-size: 20px;
  }

  
}

</style>
