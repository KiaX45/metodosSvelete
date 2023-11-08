<script>
  //importamos el componente
  import { onMount } from "svelte";
  //creamos una variable para guardar los datos
  import PrimerPuntoBiseccion from "./routes/components/PrimerPuntoBiseccion.svelte";
  import ApiPrimerPuntoFalsa from "./routes/components/Api/ApiPrimerPuntoFalsa.svelte";

  //importamos el modal
  import BiseccionPrimerPunto from "./routes/components/forms/BiseccionPrimerPunto.svelte";
  //importamos el segundo modal
  import FormularioFalsaPrimerPunto from "./routes/components/forms/FormularioFalsaPrimerPunto.svelte";
  //funciones para poder controlar el modal que pide los datos de la Api
  let showModal = false;
  let showComponent = false;

  let showModalfalsa1P = false;
  let showComponentfalsa1P = false;

	let componentKey = 1;

	function toggleModal() {
		showModal = !showModal;
	}

  function toggleModalfalsa1P() {
    showModalfalsa1P = !showModalfalsa1P;
  }

	let formData = {}; // Aquí almacenarás los datos del formulario

  function handleFormSubmit(event) {
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponent = true;
    toggleModal(); // Cierra el modal después de enviar el formulario
  }

  function handleFormSubmitfalsa1P(event) {
    formData = event.detail; // Nuevos datos del formulario
    console.log(formData);
    componentKey++; // Incrementa la clave para forzar la recreación del componente
    showComponentfalsa1P = true;
    toggleModalfalsa1P(); // Cierra el modal después de enviar el formulario
  }

  const ocultar = () => {
    showComponent = false;
    showComponentfalsa1P = false;
  };
</script>

<main>
	<nav class="navbar navbar-expand-lg bg-body-tertiary">
		<div class="container-fluid">
			<a class="navbar-brand" href="#">Metodos Númericos Aplicativos</a>
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
						<a class="nav-link active" aria-current="page" href="#">Home</a>
					</li>
				</ul>
			</div>
		</div>
	</nav>

	<div class="container text-center" style="width: 100%;">
		<div class="row">
			<div class="col-4">
				Parte de seleccion
				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método de Bisección Primer Punto</h5>
						<button class="btn btn-primary" on:click={toggleModal}>
							Calcular
						</button>
					</div>
				</div>

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método Falsa pocisión Primer Punto</h5>
						<button class="btn btn-primary" on:click={toggleModalfalsa1P}>
							Calcular
						</button>
					</div>
				</div>

        <div class="card" style="width: auto;">
          <div class="card-body">
            <h5 class="card-title">Método tres</h5>
            <a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
          </div>
        </div>
        <br />

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método tres</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método tres</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método tres</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método tres</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>
			</div>

			<div class="col">
				Parte de visualizacion
				<div class="card" style="width: 100%; height: max-content;">
					<div class="card-body">
						<h5 class="card-title">Resutado de la operación</h5>
						<div class="card" style="width: 100%; height: 100%;">
							<div class="card-body">
								<h5 class="card-title">Resultado No. 1</h5>
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
										<div class="card" style="width: 100%; height: 33vh;">
											<div class="card-body">
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
										<div class="card" style="width: 100%; height: 33vh;">
											<div class="card-body">
												<h5 class="card-title">Interpretación de resultados</h5>
												<p class="card-text">Interpretación aquí</p>
											</div>
										</div>
									{/key}
								{/if}
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Componente de modal que se muestra u oculta basado en la variable showModal -->
	{#if showModal}
		<BiseccionPrimerPunto on:submit={handleFormSubmit} />
	{/if}

  {#if showModalfalsa1P}
    <FormularioFalsaPrimerPunto on:submit={handleFormSubmitfalsa1P} />
  {/if}

	<br />

	<div class="card text-center" style="width: 100%;">
		<div class="card-header">
			Ingeniería de Sistemas - Universidad de Nariño
		</div>
		<div class="card-body">
			<h5 class="card-title">
				Realizado y desarrollado por Luis Medina, Yesid Bolaños, Gabriel Peña
			</h5>
			<p class="card-text">Todos los derechos reservados</p>
			<button class="btn btn-primary">Volver al inicio</button>
		</div>
		<div class="card-footer text-body-secondary">2023 © YLG Corporation</div>
	</div>

	<br />
	{#if showComponent}
		{#key componentKey}
			<PrimerPuntoBiseccion
				{componentKey}
				ncs={formData.ncs}
				es={formData.es}
				xi={formData.xi}
				xs={formData.xs}
			/>
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
    {/key}
  {/if}
</main>

<style>
</style>
