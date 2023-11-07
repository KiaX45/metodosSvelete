<script>
  import { onMount } from 'svelte';

  let iteraciones = [];

  onMount(async () => {
    const urlApi = 'https://metodos-production.up.railway.app/primer'; 
    const response = await fetch(urlApi, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        "ncs": 4,
        "es": 0,
        "xi": 0,
        "xs": 1.3
      }),
    });

    if (response.ok) {
      const data = await response.json();
      iteraciones = data.data.iteraciones;
    } else {
      console.error('Error al realizar la solicitud:', response.status);
    }
  });
</script>

<main>
  <h1>Resultados de la API</h1>
  <table class="table">
    <thead>
      <tr>
        <th>Número de Iteración</th>
        <th>xi</th>
        <th>xs</th>
        <th>xr</th>
        <th>fxi</th>
        <th>fxr</th>
        <th>Error (%)</th>
      </tr>
    </thead>
    <tbody>
      {#each iteraciones as iteracion}
        <tr>
          <td>{iteracion.numeroIteracion}</td>
          <td>{iteracion.xi}</td>
          <td>{iteracion.xs}</td>
          <td>{iteracion.xr}</td>
          <td>{iteracion.fxi}</td>
          <td>{iteracion.fxr}</td>
          <td>{iteracion.e}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</main>

<style>
  /* Tus estilos aquí */
</style>
