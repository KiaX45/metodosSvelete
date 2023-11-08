<script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";

  // Props que recibirá del componente padre
  export let ncs = 4;
  export let es = 0;
  export let xi = 0;
  export let xs = 1.3;

  let iteraciones = [];
  const dispatch = createEventDispatcher();
  console.log({ ncs, es, xi, xs });
  onMount(async () => {
    const urlApi = "https://metodos-production.up.railway.app/primer";
    const response = await fetch(urlApi, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ ncs, es, xi, xs }),
    });

    if (response.ok) {
      const data = await response.json();
      iteraciones = data.data.iteraciones;
      dispatch("loaded", iteraciones); // Emitir un evento con las iteraciones cargadas
    } else {
      console.error("Error al realizar la solicitud:", response.status);
    }
  });
</script>

<main>
  <h1>Biseccion primer punto</h1>
  <table class="table table-dark table-hover">
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
