<script>
  import Scroller from "@sveltejs/svelte-scroller";
  import DebugScroller from "./components/DebugScroller.svelte";
  import { onMount } from "svelte";

  let count;
  let index;
  let offset;
  let progress;
  let top = 0.1;
  let threshold = 0.5;
  let bottom = 0.9;

  let years = ["1997", "1998", "2001", "2001", "2007","2007", "2010", "2011","2015", "2016", "2023", "2023"];
  let iframes = [
    "https://datawrapper.dwcdn.net/QA8Qh/1/",
    "https://datawrapper.dwcdn.net/hputn/3/",
    "https://datawrapper.dwcdn.net/AT22n/1/",
    "https://datawrapper.dwcdn.net/Q10dh/1/",
    "https://datawrapper.dwcdn.net/17jj7/1/",
    "https://datawrapper.dwcdn.net/2uwHx/1/", 
    "https://datawrapper.dwcdn.net/RGbPd/1/",
    "https://datawrapper.dwcdn.net/fcExK/1/",
    "https://datawrapper.dwcdn.net/6aHnQ/2/",
    // "https://datawrapper.dwcdn.net/6aHnQ/2/",
    "https://datawrapper.dwcdn.net/E6kyj/1/",
    "https://datawrapper.dwcdn.net/nXLtD/1/"
    // "https://datawrapper.dwcdn.net/04JpA/1/"
  ];

  let icons = {
    1998: "icon_1998.png",
    2001: "icon_2001.png",
    2007: "icon_2007.png",
    2010: "icon_2010.png",
    2015: "icon_2014.png",
    2016: "icon_2016.png",
    2023: "icon_2023.png",
  };

  let uniqueYears = [...new Set(years)];
  let showTimeline = false;
  let headerElement;

  const handleScroll = () => {
      if (headerElement) {
        const headerBottom = headerElement.getBoundingClientRect().bottom;
      }
    };

  onMount(() => {
    window.addEventListener('scroll', handleScroll);
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  });
</script>
<body>
  <main>
    <div class="header" bind:this={headerElement}>
      <img src="/images/logo_moderno.png" width="150" alt="icono moderno" />
      <h3 class="headline">La evolución según Apple</h3>
      <p class="bajada">Una historia a través de la visualización datos</p>
      <h3 class="anios">1976</h3>
      <img src="/images/icon_apple1.png" width="150" alt="icono apple1" />
      <p class="textoheader">Apple, la empresa fundada por Steve Jobs, Steve Wozniak y Ronald Wayne, nació en el garaje de los padres de Jobs en Cupertino, 1976. Su primer producto, conocido como el <b>Apple I</b>, consistía en un ordenador personal que combinaba un microprocesador con una conexión para un teclado y un ratón.</p>
      <h3 class="anios">1980</h3>
      <img src="/images/icon_1984.png" width="100" alt="icono macintosh" />
      <p class="textoheader">El 12 de diciembre de 1980, Apple salió a la bolsa. En pocos minutos, se vendieron 4,6 millones de acciones a $22 cada una, aumentando el capital de Apple en $100 millones.</p>
      <p class="dato">Si hubieras comprado una acción de Apple en 1980, hoy tendrías 224 acciones, valoradas en $46.368</p> 
      <h3 class="anios">1985</h3>
      <p class="textoheader">Apple solicita la renuncia a Steve Jobs. Después de esto, Apple continúa pero se estanca y llegó a estar cerca de la quiebra.</p>
      <!-- por una inversión de 81,62 si lo actualizamos a la inflación. -->
      <p class="anios">Descubramos qué sucedió a lo largo de estos años:</p>

    </div>

    <div class="timeline {progress < 1 ? 'visible' : ''}">
      {#each uniqueYears as year, i}
        <div class="timeline-item">
          <span class="year-text {years[index] == year ? 'active' : 'grey'}">{year}</span>
          {#if years[index] == year && icons[year]}
            <img src="/images/{icons[year]}" alt={year} class="{year === '2023' ? 'large-icon' : ''}" />
          {/if}
        </div>
      {/each}
    </div>

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
        {#if iframes[index]}
          <iframe title="Ingresos por segmentos" aria-label="Interactive area chart" id="datawrapper-chart" src="{iframes[index]}" scrolling="no" frameborder="0" style="width: 100%; border: none;" height="700" data-external="1"></iframe>
          <script type="text/javascript">!function(){"use strict";window.addEventListener("message",(function(a){if(void 0!==a.data["datawrapper-height"]){var e=document.querySelectorAll("iframe");for(var t in a.data["datawrapper-height"])for(var r=0;r<e.length;r++)if(e[r].contentWindow===a.source){var i=a.data["datawrapper-height"][t]+"px";e[r].style.height=i}}}))}();
          </script>
        {/if}
      </div>

      <div slot="foreground" class="foreground_container">
        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">En 1997, la directiva de Apple solicita a Jobs que regrese.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Con el regreso de Steve Jobs, Apple lanzó el <b>iMac G3</b>, una computadora todo en uno que destacaba por su diseño único y colorido. El iMac no solo fue un éxito comercial, revitalizando las finanzas de Apple, sino que también simbolizó el renacimiento de la marca Apple como sinónimo de innovación.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Apple presentó el <b>iPod</b>, un reproductor de audio digital. Un producto que revoluciona la industria de la música digital.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Entre 2003 y 2006, los precios de las acciones de Apple subieron de USD 6 a mas de USD 80 por acción. Un aumento porcentual de 1233.33%, esta subida tan grande se le puede atribuir a las ventas del iPod.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">El 9 de enero de 2007, Steve Jobs anunció que iba a presentar tres productos: “un iPod con gran pantalla táctil, un teléfono móvil revolucionario, y un dispositivo avanzado de comunicación conectado a Internet”. Esos tres productos eran uno solo: El <b>iPhone</b>.</p>
          </div>
        </section>
        
        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Las acciones de Apple se dispararon a un máximo histórico de USD 97 por acción.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Steve Jobs vuelve a sorprender al mundo con el anuncio de <b>iPad</b>.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Este año marcó el fallecimiento de Steve Jobs, pero también fue el año en el que Apple se convirtió en la empresa más valiosa del mundo. Tim Cook asume como CEO.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Tim Cook anuncia el <b>Apple Watch</b>, convirtiendose en el reloj más vendido a nivel mundial en 2017.</p>
          </div>
        </section>

        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Apple reinventa los audífonos inalámbricos con los <b>AirPods</b>.</p>
          </div>
        </section>
        <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Anunciando la fecha de lanzamiento del <b>Vision Pro</b> Tim Cook explicó: "Apple Vision Pro es el dispositivo de electrónica de consumo más avanzado jamás creado. Su revolucionaria y mágica interfaz de usuario redefinirá cómo nos conectamos, creamos y exploramos".</p>
          </div>
        </section>
        <!-- <section class="step_foreground">
          <div class="epi_foreground">
            <p class="texto">Las acciones de Apple aumentaron un 1,5% en las primeras operaciones del lunes tras el anuncio de la fecha de lanzamiento del Vision Pro. Apple es la primera empresa que alcanza un valor de mercado de más de 3 billones de dólares</p>
          </div>
        </section> -->
      </div>
    </Scroller>
  </main>

  <footer class="footer">
    <p class="logos">Actualidad</p>
    <p class="textoheader">En la actualidad, Apple se mantiene como una de las empresas tecnológicas más influyentes y valiosas del mundo. Desde su modesto comienzo en un garaje hasta convertirse en la primera compañía en alcanzar un valor de mercado de más de 3 billones de dólares, Apple continúa liderando la industria con innovaciones revolucionarias. Con productos icónicos como el iPhone, el iPad, el Apple Watch y el reciente Vision Pro, la visión de Apple sigue inspirando a millones de personas alrededor del mundo.</p>

    <p class="logos">Evolución de los logos a lo largo de los años</p>
    <img src="images/applelogos.png" alt="logos" />
  </footer>

</body>

<style>
.footer {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    width: 100%;
    padding: 20px;
    padding-top: 700px;
  }
  
  .logos {
    font-size: 50px;
    line-height: 1.2;
    font-weight: bold;
    margin: 20px;
    color: #cecece;
    padding: 20px;
    font-family: Roboto, 'Helvetica', sans-serif;
  }
  
  .header {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    margin-top: 50px;
    margin-bottom: 80px;
    font-family: Roboto, 'Helvetica', sans-serif;
    text-align: center;
    padding: 20px; 
  }
  
  .headline {
    font-size: 100px;
    line-height: 1.2;
    font-weight: bold;
    margin: 20px;
    color: #cecece;
    padding: 20px;
  }
  
  .dato {   
    font-size: 40px;   
    line-height: 1.2;   
    font-weight: bold;   
    margin: 20px;   
    color: #cecece;   
    padding: 40px;   
    border: 2px solid transparent;    
    position: relative;   
    z-index: 1; 
    padding: 20px; 
  }  
    
  .dato::before {   
    content: '';   
    position: absolute;   
    top: -10px;   
    left: -10px;   
    right: -10px;   
    bottom: -10px;   
    border: 2px solid transparent;   
    border-image: linear-gradient(45deg, #e97c10, #ff0095, #1910c5, #7706b9, #00aaff) 1;   
    box-shadow: 0 0 20px rgba(255, 0, 255, 0.5),               0 0 20px rgba(255, 0, 0, 0.5),               0 0 20px rgba(255, 255, 0, 0.5),               0 0 20px rgba(0, 255, 0, 0.5),               0 0 20px rgba(0, 255, 255, 0.5),               0 0 20px rgba(0, 0, 255, 0.5),               0 0 20px rgba(255, 0, 255, 0.5);   
    z-index: -1;   
    border-radius: 10px; 
  }
  
  .bajada {
    font-size: 40px;
    font-weight: bold;
    margin: 10px;
    color: #acabab;
    font-family: Roboto, 'Helvetica', sans-serif;
    padding: 20px;
  }
  
  .descubrir {
    font-size: 30px;
    margin: 10px;
    color: #acabab;
    font-family: Roboto, 'Helvetica', sans-serif;
    padding: 80px; 
  }
  
  .anios {
    font-size: 40px;
    font-weight: bold;
    color: #ffffff;
    font-family: Roboto, 'Helvetica', sans-serif;
    padding: 20px; 
  }
  
  .textoheader {
    font-size: 20px;
    text-align: center;
    max-width: 740px;
    font-family: Roboto, 'Helvetica', sans-serif;
    padding: 50px; 
  }
  
  .texto {
    font-size: 20px;
    text-align: center;
    max-width: 740px;
    font-family: Roboto, 'Helvetica', sans-serif;
    background-color: rgba(0, 0, 0, 0.5); /* Fondo negro */
    color: #fff; /* Color de texto blanco */
    border: 2px solid #fff; /* Borde blanco */
    padding: 20px; /* Espacio interior */
    border-radius: 10px; /* Suavizar esquinas del borde */
  }
  
  .foreground_container {
    pointer-events: none;
        display: flex;
        flex-direction: column;
    justify-content: flex-start;
    align-items: flex-end;
  }
  
  .step_foreground {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    color: rgb(255, 255, 255);
    padding: 1em;
    margin: 0;
  }
  
  .epi_foreground {
    padding: 20px;
    max-width: 500px;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
  }
  
  .image_container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  
  .timeline {
    position: fixed;
    left: 20px; 
    top: 50%;
    transform: translateY(-50%);
    font-size: 30px;
    font-weight: bold;
    background-color: rgba(0, 0, 0, 0.8);
    padding: 10px;
    border-radius: 5px;
    z-index: 1000;
    display: none; 
  }
  
  .timeline.visible {
    display: block;
  }
  
  .timeline-item {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
  }
  
  .timeline-item img {
    width: 70px;
    margin-left: 10px;
  }
  
  .timeline-item .large-icon {
    width: 100px;
    height: auto;
  }
  
  .year-text {
    transition: font-size 0.3s ease, color 0.3s ease;
  }
  
  .year-text.grey {
    color: rgba(90, 90, 90, 0.767);
  }
  
  .year-text.active {
    font-size: 50px;
    color: rgb(255, 255, 255);
  }
  
</style>

<!-- ajustar titulos
marcar anos del grafico
logo al final 
claridad en los graficos, acento en los graficos
unifocar unidades de Ingresos (eeuu)
sacar el enmarcado
max width (1600 pixeles)
la historia de apple en numeros
una historia a traves de datos
muy pesado para un destacado, el destacado de los anios 
icono iphone mas chico-->