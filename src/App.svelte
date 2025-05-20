<script>
  let nombre = '';
  let mostrarModal = false;

  function animarBoton(event, tipo) {
    const boton = event.currentTarget;
    boton.style.transform = '';
    boton.style.animation = '';

    switch (tipo) {
      case 'saltar':
        boton.style.animation = 'saltar 0.5s';  
        break;
      case 'flotar':
        boton.style.transform = 'translateY(-5px)';
        break;
      case 'girar':
        boton.style.transform = 'rotate(5deg)';
        break;
      case 'inclinar':
        boton.style.transform = 'skewX(-10deg)';
        break;
    }
  }

  function resetearAnimacion(event) {
    const boton = event.currentTarget;
    boton.style.transform = '';
    boton.style.animation = '';
  }
</script>

<style>
  .app-container {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  header {
    background: linear-gradient(to right, #f72585, #7209b7);
    color: white;
    text-align: center;
    padding: 2rem;
    font-size: 2rem;
    font-weight: bold;
  }

  .main-content {
    flex: 1;
    padding: 2rem;
  }

  .contenedor-botones {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 2rem;
  }

  .boton {
    padding: 0.8rem 1.5rem;
    border: none;
    border-radius: 8px;
    color: white;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    transition: transform 0.3s ease;
  }

  .boton-saltarin { background-color: #3a86ff; }
  .boton-flotante { background-color: #4cc9f0; }
  .boton-giratorio { background-color: #f8961e; }
  .boton-inclinado { background-color: #f94144; }
  .boton-enviar {
    width: 100%;
    background: linear-gradient(to right, #43aa8b, #4cc9f0);
    margin-top: 1rem;
  }

  @keyframes saltar {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
  }

  .formulario {
    max-width: 400px;
    margin: 2rem auto;
    background:rgb(89, 114, 107);
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 12px rgb(91, 136, 150);
  }

  .formulario label {
    font-weight: bold;
    margin-bottom: 0.5rem;
    display: block;
  }

  .formulario input {
    width: 100%;
    padding: 0.75rem;
    margin-top: 0.3rem;
    border: 1px solid #ccc;
    border-radius: 6px;
  }

  .boton-modal {
    display: block;
    margin: 2rem auto;
    background: linear-gradient(to right, #7209b7, #f72585);
    padding: 1rem 2rem;
    border: none;
    border-radius: 10px;
    font-size: 1rem;
    color: white;
    cursor: pointer;
  }

  .modal {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background: rgba(94, 88, 88, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }

  .modal-contenido {
    background:rgb(228, 151, 153);
    padding: 2rem;
    border-radius: 10px;
    text-align: center;
    max-width: 400px;
    width: 90%;
  }

  .boton-cerrar {
    background: linear-gradient(to right, #f94144, #f8961e);
    border: none;
    padding: 0.8rem 1.5rem;
    border-radius: 8px;
    color: white;
    font-weight: bold;
    margin-top: 1rem;
  }

  .footer-scroll {
    background: linear-gradient(to bottom,rgb(83, 63, 63), #1a3a32);
    color: white;
    text-align: center;
    padding: 4rem 2rem;
  }

  .scroll-final {
    height: 100vh;
    background: linear-gradient(to bottom,rgb(255, 255, 255),rgb(0, 0, 0));
    color: white;
    text-align: center;
    padding-top: 120vh;
    font-size: 1.5rem;
  }
</style>

<div class="app-container">
  <header>svelte </header>

  <div class="main-content">
    <div class="contenedor-botones">
      <button 
        class="boton boton-saltarin"
        on:mouseenter={(e) => animarBoton(e, 'saltar')}
        on:mouseleave={resetearAnimacion}>
        Botón Saltarín
      </button>

      <button 
        class="boton boton-flotante"
        on:mouseenter={(e) => animarBoton(e, 'flotar')}
        on:mouseleave={resetearAnimacion}>
        Botón Flotante
      </button>

      <button 
        class="boton boton-giratorio"
        on:mouseenter={(e) => animarBoton(e, 'girar')}
        on:mouseleave={resetearAnimacion}>
        Botón Giratorio
      </button>

      <button 
        class="boton boton-inclinado"
        on:mouseenter={(e) => animarBoton(e, 'inclinar')}
        on:mouseleave={resetearAnimacion}>
        Botón Inclinado
      </button>
    </div>

    <div class="formulario">
      <label>Nombre:</label>
      <input type="text" bind:value={nombre} placeholder="Escribe tu nombre..." />
      <button class="boton boton-enviar" on:click={() => alert(`Hola ${nombre || 'desconocido'}!`)}>
        Enviar
      </button>
    </div>

    <button class="boton-modal" on:click={() => mostrarModal = true}>
      ¿Quieres ver un modal bonito?
    </button>
  </div>

  {#if mostrarModal}
    <div class="modal">
      <div class="modal-contenido">
        <h3>¡Qué bonito modal, no?</h3>
        <p>Y todo esto hecho con Svelte puro 😉</p>
        <button class="boton-cerrar" on:click={() => mostrarModal = false}>
          Cerrar
        </button>
      </div>
    </div>
  {/if}

  <div class="scroll-final">
    <h2>Mira de puro svelt 💪</h2>
    <p>no se que ejemplos mas poner</p>
  </div>
</div>
