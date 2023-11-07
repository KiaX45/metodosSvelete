<script>
	//importamos el componente 
	import { onMount } from 'svelte';
	//creamos una variable para guardar los datos
	import PrimerPuntoBiseccion from './routes/components/PrimerPuntoBiseccion.svelte';


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
						<h5 class="card-title">Método de Bisección</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método dos</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>

				<div class="card" style="width: auto;">
					<div class="card-body">
						<h5 class="card-title">Método tres</h5>
						<a href="#" class="btn btn-primary" style="color: white;">Vamos!</a>
					</div>
				</div>
				<br />

				<div class="card" style="width: auto; height: max-content">
					<div class="card-body">
						<h5 class="card-title">Ingrese los datos</h5>
						<br />
						<form>
							<div class="mb-3">
								<label for="exampleInputNcs" class="form-label"
									>No. cifras significativas</label
								>
								<input
									type="email"
									class="form-control"
									id="exampleInputNcs"
									aria-describedby="emailHelp"
								/>
								<div id="ncsHelp" class="form-text">
									Ingrese el número de cifras significativas para su cálculo
								</div>
							</div>
							<div class="mb-3">
								<label for="exampleInputXi" class="form-label">Xi</label>
								<input
									type="email"
									class="form-control"
									id="exampleInputXi"
									aria-describedby="emailHelp"
								/>
								<div id="xiHelp" class="form-text">
									Ingrese el limite inferior
								</div>
							</div>
							<div class="mb-3">
								<label for="exampleInputXs" class="form-label">Xs</label>
								<input
									type="email"
									class="form-control"
									id="exampleInputXs"
									aria-describedby="emailHelp"
								/>
								<div id="xsHelp" class="form-text">
									Ingrese el limite superior
								</div>
							</div>

							<button type="submit" class="btn btn-primary">Calcular</button>
						</form>
					</div>
				</div>
			</div>
			<div class="col">
				Parte de visualizacion
				<div class="card" style="width: 100%; height: max-content;">
					<div class="card-body">
						<h5 class="card-title">Resutado de la operación</h5>
						<div class="card" style="width: 100%; height: 33vh;">
							<div class="card-body">
								<h5 class="card-title">Resultado No. 1</h5>
								<p class="card-text">Aqui va el resultado</p>
							</div>
						</div>
						<br />
						<div class="card" style="width: 100%; height: 33vh;">
							<div class="card-body">
								<h5 class="card-title">Resultado No. 2</h5>
								<p class="card-text">Aqui va el resultado</p>
							</div>
						</div>
						<br />
						<div class="card" style="width: 100%; height: 33vh;">
							<div class="card-body">
								<h5 class="card-title">Interpretación de resultados</h5>
								<p class="card-text">Interpretación aquí</p>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>

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

	<div>
		Componente que se deberia ver al final
		<PrimerPuntoBiseccion />
	</div>

</main>

<style>

</style>
