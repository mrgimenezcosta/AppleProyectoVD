<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import DebugScroller from "./components/DebugScroller.svelte";
  import { onMount } from "svelte";

  /* Variables para el scroller */
  let count;
  let index;
  let offset;
  let progress;
  let top = 0.1;
  let threshold = 0.5;
  let bottom = 0.9;

  /* Charts */
  let charts = {
    0: "barra_1980.png",
    1: "lineas_stock_1984.png",
    2: "lineas_stock_1984.png",
    3: "lineas_stock_1984.png",
    4: "lineas_stock_1998.png",
    5: "lineas_income_1998.png"
  };

  let years = ["1980", "1984", "1984", "1984", "1985", "1997", "1998", "1998", "2001", "2001", "2007", "2007", "2010", "2010", "2011"];

  // Variable para manejar la visibilidad del timeline
  let showTimeline = false;

  // Elemento de referencia para el header
  let headerElement;

  // Verificar la posición del scroll
  const handleScroll = () => {
    if (headerElement) {
      const headerBottom = headerElement.getBoundingClientRect().bottom;
      showTimeline = headerBottom < 0;
    }
  };

  // Montar el evento de scroll
  onMount(() => {
    window.addEventListener('scroll', handleScroll);
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });
</script>

<main>
  <div class="header" bind:this={headerElement}>
    <img src="/images/primer_logo.png" width="100" alt="primer logo" />
    <h3 class="headline">
      <b>Apple Computer Company</b>
      Think different.
    </h3>
    <p class="bajada">La evolución según Apple.</p>
    <h3 class="anios">1976</h3>
    <p class="texto">Apple, la empresa fundada por Steve Jobs, Steve Wozniak y Ronald Wayne, vio la luz en el garaje de los padres de Jobs en Cupertino, 1976. Su primer producto, conocido como el <b>Apple I</b>, consistía en un ordenador personal que combinaba un microprocesador con una conexión para un teclado y un ratón.</p>
    <img src="/images/primer_anuncio.png" width="600" alt="primer publicidad de apple" />
  </div>

  {#if progress < 1}
  <DebugScroller index={index} count={count} offset={offset} progress={progress} />
  {/if}

  <!-- Timeline -->
  <div class="timeline" class:visible={showTimeline}>
    <h3>{years[index]}</h3>
  </div>

  <!-- Scroller -->
  <Scroller
    top={top}
    threshold={threshold}
    bottom={bottom}
    bind:count={count}
    bind:index={index}
    bind:offset={offset}
    bind:progress={progress}
  >
    <div slot="background" class="image_container">
      <img src="/images/{charts[index]}" height="700" alt="chart {index}" class="charts" />
    </div>
    <div slot="foreground" class="foreground_container">
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Entre septiembre de 1977 y septiembre de 1980, las ventas anuales crecieron de 775.000 dólares a 118 millones de dólares, una tasa de crecimiento anual promedio del 533%.</p>
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Uno de los eventos que marcó el gran éxito de la compañía y que es uno de los principales hitos de la historia de Apple es la presentación del <b>Macintosh</b>, que se llevó a cabo el 24 de enero de 1984, de la mano de Steve Jobs. De hecho, a raíz de esta presentación se empezó a ver un cambio, de cierta manera, radical en el mundo de la informática, ya que este dispositivo se considera el primer ordenador personal con interfaz gráfica.</p>
        </div>
      </section>
      <section class="step_foreground_foto">
        <div class="epi_foreground_foto">
          <img src="/images/macintosh.png" width="600" alt="primer publicidad de apple" />
        </div>
      </section>
      <section class="step_foreground_foto">
        <div class="epi_foreground_foto">
          <video width="800" style="margin-bottom: 80px;" controls>
            <source src="/images/anuncioMacintosh.mp4" type="video/mp4">
            <track kind="captions" src="/videos/subtitulos.vtt" srclang="es" label="Español">
            Tu navegador no soporta la reproducción de videos.
          </video>
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Apple solicita la renuncia a Steve Jobs. Despues de esto, Apple continua pero se estanca y llegó a estar cerca de la quiebra.</p>
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">En 1997, la directiva de Apple solicita a Jobs que regrese.</p>
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Con el regreso de Steve Jobs, Apple lanzó el iMac G3, una computadora todo en uno que destacaba por su diseño único y colorido. El iMac no solo fue un éxito comercial, revitalizando las finanzas de Apple, sino que también simbolizó el renacimiento de la marca Apple como sinónimo de innovación y diseño de vanguardia. Este fue solo el comienzo de una serie de productos que transformarían industrias enteras.</p>
        </div>
      </section>
      <section class="step_foreground_foto">
        <div class="epi_foreground_foto">
          <img src="/images/ImacG3.png" width="600" alt="G3" />
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Apple presentó el iPod, un reproductor de audio digital. Un producto que revolucionan la industria de la música digital.</p>
        </div>
      </section>
      <section class="step_foreground_foto">
        <div class="epi_foreground_foto">
          <img src="/images/Ipod1.png" width="300" alt="G3" />
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Steve Jobs anunció que iba a presentar tres productos: “un iPod con gran pantalla táctil, un teléfono móvil revolucionario, y un dispositivo avanzado de comunicación conectado a Internet”. Esos tres productos eran uno solo: El Iphone.</p>
        </div>
      </section>
      <section class="step_foreground_foto">
        <div class="epi_foreground_foto">
          <img src="/images/Iphone1.png" width="400" alt="G3" />
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">A tres años de haber hecho historia con la presentación del primer iPhone, Steve Jobs volvía a sorprender al mundo con el anuncio de iPad</p>
        </div>
      </section>
      <section class="step_foreground_foto">
        <div class="epi_foreground_foto">
          <img src="/images/Ipad1.png" width="800" alt="G3" />
        </div>
      </section>
      <section class="step_foreground">
        <div class="epi_foreground">
          <p class="texto">Este año marco el fallecimiento de Steve Jobs, pero también fue el año en el que Apple se convirtio en la empresa más valiosa del mundo.</p>
        </div>
      </section>
    </div>
  </Scroller>
</main>

<style>
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 50px;
    margin-bottom: 80px;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
  }

  .headline {
    font-size: 30px;
    line-height: 1.2;
    font-weight: normal;
    text-align: center;
    margin: 20px;
    color: #333;
  }

  .bajada {
    font-size: 25px;
    font-weight: normal;
    text-align: center;
    margin: 10px;
    color: #666;
  }

  .anios {
    font-size: 40px;
    font-weight: bold;
    text-align: center;
    color: #333;
  }

  .headline b {
    display: block;
    font-size: 32px;
  }

  /* Estilos para el scroller */
  .foreground_container {
    pointer-events: none;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-end;
    padding-right: 50px; /* Ajusta este valor según sea necesario */
  }

  .step_foreground,
  .step_foreground_foto {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    color: black;
    padding: 1em;
    margin: 0;
  }

  .epi_foreground {
    padding: 20px;
    max-width: 500px;
    background-color: rgba(255, 255, 255, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    margin: auto; /* Centramos horizontalmente */
    border-radius: 10px;
  }

  .epi_foreground_foto {
    padding: 20px;
    text-align: center; /* Centramos el contenido */
    background-color: transparent;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .texto {
    margin-bottom: 50px;
    max-width: 740px;
  }

  .image_container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .timeline {
    position: fixed;
    left: 20px; /* Ajusta este valor según sea necesario */
    top: 50%;
    transform: translateY(-50%);
    font-size: 30px;
    font-weight: bold;
    background-color: rgba(255, 255, 255, 0.8);
    padding: 10px;
    border-radius: 5px;
    z-index: 1000;
    display: none; /* Ocultar inicialmente */
  }

  .timeline.visible {
    display: block; /* Mostrar cuando se cumplan las condiciones */
  }
</style>
