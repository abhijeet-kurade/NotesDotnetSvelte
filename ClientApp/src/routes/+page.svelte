<script>
  import {onMount} from 'svelte';
  let some = "aaa"
  let name = [];

  function refresh_data(){
  fetch('http://localhost:5125/api/WeatherForecast/GetWeather')
  .then(response => response.json())
  .then( data => {
  name = data;
  });
  }

  onMount(async() => {
  refresh_data();
  });


</script>

<main>
  <h2>
    {some}
  </h2>
  
<style>
  table {
    border-collapse: collapse;
    width: 100%;
  }

  th, td {
    border: 1px solid black;
    padding: 8px;
    text-align: left;
  }

  th {
    background-color: #f2f2f2;
  }
</style>
  <table>
    <thead>
      <tr>
        <th>Date</th>
        <th>Temperature (C)</th>
        <th>Temperature (F)</th>
        <th>Summary</th>
      </tr>
    </thead>
    <tbody>
      {#each name as node}
      <tr>
        <td>{node.date}</td>
        <td>{node.temperatureC}</td>
        <td>{node.temperatureF}</td>
        <td>{node.summary}</td>
      </tr>
      {/each}
    </tbody>
  </table>
</main>
