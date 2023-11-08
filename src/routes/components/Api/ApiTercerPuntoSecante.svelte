<script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";

  // Props que recibirá del componente padre
  export let ncs = 4;
  export let xi = 0;
  export let xi0 = 1.3;

  let iteraciones = [];
  const dispatch = createEventDispatcher();
  console.log({ncs, xi, xi0});
  onMount(async () => {
    const urlApi = "https://metodos-production.up.railway.app/Secante3P";
    const response = await fetch(urlApi, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ ncs, xi, xi0 }),
    });

    if (response.ok) {
      const data = await response.json();
      iteraciones = data.data.resultados;
      dispatch("loaded", iteraciones); // Emitir un evento con las iteraciones cargadas
    } else {
      console.error("Error al realizar la solicitud:", response.status);
    }
  });
</script>

<main>
  <h1>Falsa pocisión primer punto</h1>
  <table class="table">
    <thead>
      <tr>
        <th>Número de Iteración</th>
        <th>xi-1</th>
        <th>xi</th>
        <th>xi+1</th>
        <th>f(xi-1)</th>
        <th>f(xi)</th>
        <th>Error (%)</th>
      </tr>
    </thead>
    <tbody>
      {#each iteraciones as iteracion}
        <tr>
          <td>{iteracion.iteracion}</td>
          <td>{iteracion.xi0}</td>
          <td>{iteracion.xi}</td>
          <td>{iteracion.fxi0}</td>
          <td>{iteracion.fxi}</td>
          <td>{iteracion.xi1}</td>
          <td>{iteracion.e}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</main>

<style>
  /* Tus estilos aquí */
</style>