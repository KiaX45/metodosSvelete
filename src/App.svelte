<script>
  //importamos el componente
  import { onMount } from "svelte";
  //creamos una variable para guardar los datos
  import PrimerPuntoBiseccion from "./routes/components/PrimerPuntoBiseccion.svelte";
  import ApiPrimerPuntoFalsa from "./routes/components/Api/ApiPrimerPuntoFalsa.svelte";
  import ApiSegundoPunto from "./routes/components/Api/ApiSegundoPunto.svelte";
  import ApiTercerPuntoBiseccion from "./routes/components/Api/ApiTercerPuntoBiseccion.svelte";
  import ApiTercerPuntoFalsa from "./routes/components/Api/ApiTercerPuntoFalsa.svelte";
  import ApiTercerPuntoNewton from "./routes/components/Api/ApiTercerPuntoNewton.svelte";
  import ApiTercerPuntoSecante from "./routes/components/Api/ApiTercerPuntoSecante.svelte";

  //importamos el modal
  import BiseccionPrimerPunto from "./routes/components/forms/BiseccionPrimerPunto.svelte";
  //importamos el segundo modal
  import FormularioFalsaPrimerPunto from "./routes/components/forms/FormularioFalsaPrimerPunto.svelte";
  import FormularioSegundoPunto from "./routes/components/forms/FormularioSegundoPunto.svelte";
  import FormularioBisec3P from "./routes/components/forms/FormularioBisec3P.svelte";
  import FormularioFalsa3P from "./routes/components/forms/FormularioFalsa3P.svelte";
  import FormularioNewton3P from "./routes/components/forms/FormularioNewton3P.svelte";
  import FormularioSecante3P from "./routes/components/forms/FormularioSecante3P.svelte";
  //funciones para poder controlar el modal que pide los datos de la Api
  let showModal = false;
  let showComponent = false;

  let showModalfalsa1P = false;
  let showComponentfalsa1P = false;

  let showModalsegundoP = false;
  let showComponentsegundoP = false;

  let showModalTercerBiseccion3P = false;
  let showComponentTercerBiseccion3P = false;

  let showModalfalsa3P = false;
  let showComponentfalsa3P = false;

  let showNewton3P = false;
  let showComponentNewton3P = false;

  let showSecante3P = false;
  let showComponentSecante3P = false;

  let componentKey = 1;

  function toggleModal() {
    showModal = !showModal;
  }

  function toggleModalfalsa1P() {
    showModalfalsa1P = !showModalfalsa1P;
  }

  function toggleModalsegundoP() {
    showModalsegundoP = !showModalsegundoP;
  }

  function toggleModalTercerBiseccion3P() {
    showModalTercerBiseccion3P = !showModalTercerBiseccion3P;
  }

  function toggleModalfalsa3P() {
    showModalfalsa3P = !showModalfalsa3P;
  }

  function toggleModalNewton3P() {
    showNewton3P = !showNewton3P;
  }

  function toggleModalSecante3P() {
    showSecante3P = !showSecante3P;
  }

  let formData = {}; // Aquí almacenarás los datos del formulario

  function handleFormSubmit(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponent = true;
    toggleModal(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitfalsa1P(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentfalsa1P = true;
    toggleModalfalsa1P(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitsegundoP(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentsegundoP = true;
    toggleModalsegundoP(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitTercerBiseccion3P(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentTercerBiseccion3P = true;
    toggleModalTercerBiseccion3P(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitfalsa3P(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentfalsa3P = true;
    toggleModalfalsa3P(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitNewton3P(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentNewton3P = true;
    toggleModalNewton3P(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitSecante3P(event) {
    ocultar();
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentSecante3P = true;
    toggleModalSecante3P(); // Cierra el modal después de enviar el formulario
  }

  const ocultar = () => {
    showComponent = false;
    showComponentfalsa1P = false;
    showComponentsegundoP = false;
    showComponentTercerBiseccion3P = false;
    showComponentfalsa3P = false;
    showComponentNewton3P = false;
    showComponentSecante3P = false;
  };
</script>

<main style="background-color: FFEED9;">
  <nav class="navbar navbar-expand-lg bg-success">
    <div class="container-fluid">
      <a class="navbar-brand text-color" href="#">Metodos Númericos Aplicativos</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon" />
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link active text-color" aria-current="page" href="#" style="color: rgb(234, 242, 0);">Home</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <br>

  <div class="container text-center">
    <div class="row row-cols-2 row-cols-lg-5 g-2 g-lg-3" style="justify-content: center;">
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método de Bisección Primer Punto</h5>
            <button class="btn btn-success" on:click={toggleModal}>
              Calcular
            </button>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método de Falsa Pocisión Primer Punto</h5>
            <button class="btn btn-success" on:click={toggleModalfalsa1P}>
              Calcular
            </button>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Segundo Punto Raíz Cúbica de un Número</h5>
            <button class="btn btn-success" on:click={toggleModalsegundoP}>
              Calcular
            </button>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método de Bisección Tercer Punto</h5>
            <button
              class="btn btn-success"
              on:click={toggleModalTercerBiseccion3P}
            >
              Calcular
            </button>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método de Falsa Posición Tercer Punto</h5>
            <button class="btn btn-success" on:click={toggleModalfalsa3P}>
              Calcular
            </button>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método de Newton-Raphson Tercer Punto</h5>
            <button class="btn btn-success" on:click={toggleModalNewton3P}>
              Calcular
            </button>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método de la Secante Tercer Punto</h5>
            <button class="btn btn-success" on:click={toggleModalSecante3P}>
              Calcular
            </button>
          </div>
        </div>
      </div>
    </div>

    <br>

    <div class="col" style="overflow-x: hidden;">
      <div class="card-showMain" style="width: 100%; height: 100%;">
        <div class="card-body">
          {#if showComponent}
            {#key componentKey}
              <PrimerPuntoBiseccion
                {componentKey}
                ncs={formData.ncs}
                es={formData.es}
                xi={formData.xi}
                xs={formData.xs}
              />
              <br />
              <div class="card-int" style="width: auto; height: 33vh;">
                <div class="card-body" style="width: auto;">
                  <h5 class="card-title">Interpretación de resultados</h5>
                  <p class="card-text">Interpretación aquí</p>
                </div>
              </div>
            {/key}
          {/if}

          {#if showComponentfalsa1P}
            {#key componentKey}
              <ApiPrimerPuntoFalsa
                {componentKey}
                ncs={formData.ncs}
                es={formData.es}
                xi={formData.xi}
                xs={formData.xs}
              />
              <br />
              <div class="card-int" style="width: 100%; height: 33vh;">
                <div class="card-body">
                  <h5 class="card-title">Interpretación de resultados</h5>
                  <p class="card-text">Interpretación aquí</p>
                </div>
              </div>
            {/key}
          {/if}
        </div>

        {#if showComponentsegundoP}
          {#key componentKey}
            <ApiSegundoPunto
              {componentKey}
              xi={formData.xi}
              ncs={formData.ncs}
              a={formData.a}
            />
          {/key}
        {/if}

        {#if showComponentTercerBiseccion3P}
          {#key componentKey}
            <ApiTercerPuntoBiseccion
              {componentKey}
              xi={formData.xi}
              ncs={formData.ncs}
              xs={formData.xs}
            />
            <br />
            <div class="card-int" style="width: 100%; height: 33vh;">
              <div class="card-body">
                <h5 class="card-title">Interpretación de resultados</h5>
                <p class="card-text">Interpretación aquí</p>
              </div>
            </div>
          {/key}
        {/if}

        {#if showComponentfalsa3P}
          {#key componentKey}
            <ApiTercerPuntoFalsa
              {componentKey}
              xi={formData.xi}
              ncs={formData.ncs}
              xs={formData.xs}
            />
            <br />
            <div class="card-int" style="width: 100%; height: 33vh;">
              <div class="card-body">
                <h5 class="card-title">Interpretación de resultados</h5>
                <p class="card-text">Interpretación aquí</p>
              </div>
            </div>
          {/key}
        {/if}

        {#if showComponentNewton3P}
          {#key componentKey}
            <ApiTercerPuntoNewton
              {componentKey}
              xi={formData.xi}
              ncs={formData.ncs}
            />
            <br />
            <div class="card-int" style="width: 100%; height: 33vh;">
              <div class="card-body">
                <h5 class="card-title">Interpretación de resultados</h5>
                <p class="card-text">Interpretación aquí</p>
              </div>
            </div>
          {/key}
        {/if}

        {#if showComponentSecante3P}
          {#key componentKey}
            <ApiTercerPuntoSecante
              {componentKey}
              xi={formData.xi}
              ncs={formData.ncs}
              xi0={formData.xi0}
            />
            <br />
            <div class="card-int" style="width: 100%; height: 33vh;">
              <div class="card-body">
                <h5 class="card-title">Interpretación de resultados</h5>
                <p class="card-text">Interpretación aquí</p>
              </div>
            </div>
          {/key}
        {/if}
      </div>
    </div>

    <!-- Componente de modal que se muestra u oculta basado en la variable showModal -->
    {#if showModal}
      <BiseccionPrimerPunto on:submit={handleFormSubmit} />
    {/if}

    {#if showModalfalsa1P}
      <FormularioFalsaPrimerPunto on:submit={handleFormSubmitfalsa1P} />
    {/if}

    {#if showModalsegundoP}
      <FormularioSegundoPunto on:submit={handleFormSubmitsegundoP} />
    {/if}

    {#if showModalTercerBiseccion3P}
      <FormularioBisec3P on:submit={handleFormSubmitTercerBiseccion3P} />
    {/if}

    {#if showModalfalsa3P}
      <FormularioFalsa3P on:submit={handleFormSubmitfalsa3P} />
    {/if}

    {#if showNewton3P}
      <FormularioNewton3P on:submit={handleFormSubmitNewton3P} />
    {/if}

    {#if showSecante3P}
      <FormularioSecante3P on:submit={handleFormSubmitSecante3P} />
    {/if}

    <br />

    <div class="card-footer text-center" style="width: 100%;">
      <div class="card-header">
        Ingeniería de Sistemas - Universidad de Nariño
      </div>
      <div class="card-body">
        <h5 class="card-title">
          Realizado y desarrollado por Luis Medina, Yesid Bolaños, Gabriel Peña
        </h5>
        <p class="card-text">
          Todos los derechos reservados
        </p>
        <button class="btn btn-success">Volver al inicio</button>
      </div>
      <br>
      <div class="card-text">
        2023 © YLG Corporation
      </div>
    </div>
  </div>
</main>

<style>

  .card-footer {
    background-color: #F7FFE5;
  }

  .navbar {
    background-color: #F99417;
    font-family: 'Times New Roman', Times, serif;
  }

  .card-showMain {
    background-color: #F6FFDE;
  }

  .card {
    background-color: #E5F9DB;
    box-shadow: 2cm;
  }

  .card-int {
    background-color: #F6FFDE;
  }

  .btn {
    background-color: #519259;
  }

  .text-color {
    color: rgb(234, 242, 0);
  }
</style>
