<style>
  body {
    font-family: Helvetica, sans-serif;
    text-align: center;
    background-color: white;
  }

  h1 {
    color: magenta;
    font-weight: bold;
    margin-top: 30px;
  }

  .carousel-container {
    position: relative;
    width: 100%;
    max-width: 600px;
    margin: 40px auto;
  }

  .model-viewer {
    display: none;
    width: 100%;
    height: 500px;
  }

  .model-viewer.active {
    display: block;
  }

  .carousel-controls {
    margin-top: 20px;
  }

  button {
    padding: 10px 20px;
    margin: 0 10px;
    font-size: 16px;
    cursor: pointer;
  }

  .description {
    font-size: 16px;
    color: #444;
    margin-top: 15px;
  }
</style>

# Insumos para la ideación

<div class="carousel-container">
  <model-viewer class="model-viewer active" src="models/model1.glb" auto-rotate camera-controls></model-viewer>
  <model-viewer class="model-viewer" src="models/model2.glb" auto-rotate camera-controls></model-viewer>
  <model-viewer class="model-viewer" src="models/model3.glb" auto-rotate camera-controls></model-viewer>
</div>

<div class="description" id="description">
  Descripción del modelo 1: Este insumo representa una primera idea conceptual.
</div>

<div class="carousel-controls">
  <button onclick="prevModel()">⟨ Anterior</button>
  <button onclick="nextModel()">Siguiente ⟩</button>
</div>

<script type="module" src="https://unpkg.com/@google/model-viewer/dist/model-viewer.min.js"></script>
<script>
  const models = document.querySelectorAll('.model-viewer');
  const descriptionBox = document.getElementById('description');
  const descriptions = [
    "Descripción del modelo 1: Este insumo representa una primera idea conceptual.",
    "Descripción del modelo 2: Iteración avanzada con mejoras funcionales.",
    "Descripción del modelo 3: Versión final enfocada en la presentación visual."
  ];
  
  let current = 0;

  function showModel(index) {
    models.forEach((model, i) => {
      model.classList.toggle('active', i === index);
    });
    descriptionBox.textContent = descriptions[index];
  }

  function nextModel() {
    current = (current + 1) % models.length;
    showModel(current);
  }

  function prevModel() {
    current = (current - 1 + models.length) % models.length;
    showModel(current);
  }
</script>
