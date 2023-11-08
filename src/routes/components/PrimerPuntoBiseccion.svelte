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
  <h3>Resultado de la Operación</h3>
  <h1>Método de Bisección Primer Punto</h1>
  <h2>f(x) = x^10 - 1 </h2>
  <p>Dado entre 0 y 1.3</p>
  <table class="table table-info table-striped table-bordered">
    <thead>
      <tr>
        <th>Iteración</th>
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
