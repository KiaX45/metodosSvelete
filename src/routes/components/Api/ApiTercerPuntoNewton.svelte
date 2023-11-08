<script>
  import { onMount } from "svelte";
  import { createEventDispatcher } from "svelte";

  // Props que recibirá del componente padre
  export let ncs = 5;
  export let xi = 4.2;

  let iteraciones = [];
  const dispatch = createEventDispatcher();
  console.log({ ncs, xi});
  onMount(async () => {
    const urlApi = "https://metodos-production.up.railway.app/Newton3P";
    const response = await fetch(urlApi, {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ ncs, xi}),
    });

    if (response.ok) {
      const data = await response.json();
      console.log(data);
      iteraciones = data.data.iteraciones; // Aquí cambiamos `data.data.iteraciones` a `data.resultados`
      console.log(iteraciones);
      dispatch("loaded", iteraciones); // Emitir un evento con las iteraciones cargadas
    } else {
      console.error("Error al realizar la solicitud:", response.status);
    }
  });
</script>

<main>
  <h3>Resultado de la Operación</h3>
  <h1>Método de Newton-Raphson Tercer Punto</h1>
  <h2>f(x) = tan(x) - 0.5x </h2>
  <table class="table table-info table-striped table-bordered">
    <thead>
      <tr>
        <th>Iteración</th>
        <th>xi</th>
        <th>f(xi)</th>
        <th>df(xi)</th>
        <th>xi+1</th>
        <th>Error (%)</th>
      </tr>
    </thead>
    <tbody>
      {#each iteraciones as iteracion}
        <tr>
          <td>{iteracion.numeroIteracion}</td>
          <td>{iteracion.xi}</td>
          <td>{iteracion.fxi}</td>
          <td>{iteracion.dfxi}</td>
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
