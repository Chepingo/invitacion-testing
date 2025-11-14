<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Invitación de Boda</title>

  <style>
    /* Fuentes utilizadas en el boceto y estilos base */
    @import url('https://fonts.googleapis.com/css2?family=Great+Vibes&display=swap');

    /* ====== ESTILO GENERAL MODIFICADO ====== */
    body {
      margin: 0;
      padding: 0;
      font-family: "Poppins", sans-serif;
    }

    /* TÍTULO - Posición ajustada para el nuevo flujo */
    .titulo {
      position: absolute;
      top: 5vh;
      left: 50%;
      transform: translateX(-50%);
      text-align: center;
      color: #fff;
      font-size: 3rem;
      z-index: 110;
      font-style: italic;
      text-shadow: 0 2px 8px rgba(0, 0, 0, 0.7);
      font-family: 'Great Vibes', cursive;
      margin: 0;
      width: 90%;
    }

    /* ====== CONTENEDOR PRINCIPAL (.hero) - Ahora contiene el fondo ====== */
    .hero {
      /* LA IMAGEN DE FONDO AHORA SOLO ESTÁ AQUÍ */
      background: url("multimedia/fotos/fondo/imagefondo.png") center/cover no-repeat;

      /* Aseguramos que abarque toda la vista inicial */
      min-height: 100vh;
      position: relative;

      /* Propiedades de Flexbox originales */
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 150px;
      width: 100%;
    }

    /* Overlay semi-transparente sobre el fondo de jardín */
    .hero::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.4);
        z-index: 10;
    }

    /* Contenedor para manejar la posición del título */
    .hero-content-wrapper {
        position: relative;
        z-index: 15;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 200px;
    }

    /* ====== BLOQUE IZQUIERDO: VIDEO ====== */
    .bloque-video {
      width: 300px;
      height: 600px;
      backdrop-filter: blur(15px);
      background: rgba(255, 255, 255, 0.062);
      border-radius: 15px;
      padding: 1rem;
      overflow: hidden;
      box-shadow: 0 4px 20px rgba(54, 54, 54, 0.5);
      position: relative;
    }

    .video-boda {
      width: 100%;
      height: 100%;
      border-radius: 15px;
      object-fit: cover;
    }

    /* ====== BLOQUE DERECHO: IMAGEN ====== */
    .bloque-imagen {
      width: 700px;
      height: 600px;
      backdrop-filter: blur(10px);
      background: rgba(255, 255, 255, 0.15);
      border-radius: 9px;
      overflow: hidden;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
      position: relative;
    }

    .imagen-rosada {
      width: 100%;
      height: 100%;
      border-radius: 8px;
      object-fit: cover;
    }

    /* ====== SEPARADOR NEGRO ====== */
    .separator-div {
        height: 50px;
        background-color: black;
        width: 100%;
        position: relative;
        z-index: 100;
    }

    /* ====== SECCIÓN DE DETALLES (NUEVA SECCIÓN) ====== */
    .celebration-details-section {
        background-color: #f7f3e8; /* Fondo amarillo pálido de la imagen */
        padding: 4rem 1rem;
        text-align: center;
    }

    .details-title {
        font-family: 'Great Vibes', cursive;
        font-size: 2.5rem;
        color: #8B5C5C; /* Tono de color principal */
        margin-bottom: 0.5rem;
    }

    .title-underline {
        width: 50%;
        max-width: 400px;
        height: 1px;
        background-color: #8B5C5C;
        margin: 0 auto 3rem;
    }

    /* NUEVO: Contenedor para manejar el split 50/50 de las tarjetas inferiores */
    .papas-container-split {
        display: flex;
        justify-content: center;
        gap: 5px; /* Espacio entre las tarjetas de padres */
        margin-top: 40px; /* Espacio entre la tarjeta de padrinos y la de padres */
    }

    /* ESTILO base para cada una de las 3 tarjetas blancas */
    .info-card {

      font-family: 'Great Vibes', cursive;
        font-size: 1.4rem;
        color: #333;
        margin-top: 5px;

        background-color: white;
        padding: 2rem;
        border-radius: 15px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        margin: 0 auto;
    }

    /* Estilo específico para la tarjeta superior de Padrinos */
    .padrinos-card {
        max-width: 1000px; /* Ocupa todo el ancho disponible del main-info-box */
        margin-bottom: 20px; /* Espacio inferior */
    }

    /* Estilos para las tarjetas de Papas (50% de ancho en desktop) */
    .papas-card {
        width: 25%; /* Ocupa casi la mitad del espacio en el contenedor split */
        /* ELIMINA: el estilo background-color: #f8f8f8; si quieres que sean blanco puro */
        /* La sombra de la caja ya viene del .info-card */
    }

   
    /* ESTILOS DE BOTONES BLANCOS (ATRIBUTOS CLAVE) */
    .button-section {
        margin-top: 4rem;
        display: flex;
        justify-content: center;
        gap: 30px; /* Espacio entre botones */
    }

    .action-button {
        /* Tamaño y Posición (Atributos para modificar) */
        padding: 12px 30px; /* Tamaño del botón */
        border: 2px solid #8B5C5C; /* Borde del botón */

        /* Estilos fijos */
        background-color: white;
        color: #8B5C5C;
        font-weight: bold;
        text-transform: uppercase;
        border-radius: 5px;
        cursor: pointer;
        transition: background-color 0.3s, color 0.3s;
    }

    .action-button:hover {
        background-color: #8B5C5C;
        color: white;
    }

    /* ====== SECCIÓN DE DETALLES (Antigua) - Se mantiene para demostrar scroll */
    .details-section {
        background-color: white;
        min-height: 50vh; /* Se reduce el alto */
        padding: 4rem 1rem;
        text-align: center;
    }


      /* ======================================= */
      /* == Estilos para la Sección de Misa == */
      /* ======================================= */

      /* Contenedor Flex para la Misa y el Mapa */
      .location-container {
          justify-content: center;
          gap: 40px; /* Espacio entre los dos contenedores de Misa */
          max-width: 1000px;
          margin: 30px auto 30px; /* Margen superior e inferior para separarlo de padres y botones */
      }

      /* Estilo base para las dos tarjetas de Misa/Mapa */
      .location-card {
          width: 45%; /* Ocupan casi la mitad del contenedor */
          padding: 1.5rem;
          flex-direction: column;
          align-items: center;
          text-align: center;
      }

      .location-title {
          font-size: 1.5rem;
          color: #8B5C5C; /* Color vino */
          margin-bottom: 1.5rem;
          align-items: center;
          justify-content: center;
      }
      .church-icon {
          font-size: 2rem;
          line-height: 1;
          margin-right: 10px;
          color: #8B5C5C;
      }

      .location-details p {
          font-family: 'Great Vibes', cursive;
          font-size: 1.2rem;
          color: #5a5a5a;
          line-height: 1.5;
      }
      .location-details .detail-highlight {
          font-size: 1.3rem;
          color: #8B5C5C;
          font-weight: bold;
      }

      /* Estilos específicos para el contenedor del mapa */
      .map-card {
          padding-top: 2rem;
      }

      .map-embed-wrapper {
          width: 100%;
          /* Altura fija para el mapa. Crucial para evitar que se colapse */
          height: 300px;
          border-radius: 8px;
          overflow: hidden;
          box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
      }

      /* ======================================= */
      /* == Estilos Específicos para el Salón == */
      /* ======================================= */

      /* 1. Contenedor Padre: Hace que los elementos internos floten uno al lado del otro */
      .location-container {
          display: flex;
          flex-direction: row; /* Coloca los hijos en una fila */
          justify-content: space-around; /* Distribuye el espacio entre el texto y el mapa */
          align-items: flex-start; /* Alinea los elementos a la parte superior */
          flex-wrap: wrap; /* Permite que se apilen en pantallas pequeñas (responsivo) */
      }

      /* 2. Contenedores Hijos: Define el tamaño y el margen para ambas tarjetas */
      /* Esta regla aplica a: .info-card.location-card (Misa info) 
                            y .info-card.location-card.map-card (Mapa) */
      .info-card.location-card {
          /* Define un ancho máximo para asegurar que dos quepan en la fila */
          max-width: 450px; 
          width: 100%; /* Permite que la tarjeta crezca hasta el max-width */
          margin: 15px 10px; /* Margen para separarlas un poco */
          box-sizing: border-box; 
      }

      /* Nota: Si el selector .location-container es demasiado genérico y afecta a otras secciones 
        que no deben ser horizontales, considera agregar una clase única al HTML como se sugirió antes,
        por ejemplo, .location-container.misa, y usar esa clase en el CSS. */

      /* Margen superior para separarlo de la Misa */
      .salon-container {
          margin-top: 50px;
      }

      /* Icono del Salón */
      .salon-icon {
          font-size: 2rem;
          line-height: 1;
          margin-right: 10px;
          color: #8B5C5C;
      }

      /* 1. Contenedor Padre: Habilita Flexbox para la disposición horizontal */
      .location-container.salon-container {
          display: flex;
          flex-direction: row; /* Coloca los elementos en una fila */
          justify-content: space-around; /* Distribuye el espacio entre los dos */
          align-items: flex-start; /* Alinea arriba para evitar que el mapa más largo lo desplace */
          flex-wrap: wrap; /* Importante para el diseño responsivo en pantallas pequeñas */
      }

      /* 2. Contenedores Hijos: Les da un tamaño máximo para que quepan dos */
      /* Ambas clases (el salón de texto y el mapa) comparten este estilo */
      .info-card.salon-location-card {
          /* Un ancho máximo para que cada uno ocupe aproximadamente la mitad del espacio disponible */
          max-width: 450px;
          width: 100%; /* Asegura que usen todo el ancho permitido dentro del max-width */
          margin: 15px 10px; /* Agrega margen vertical y horizontal */
          box-sizing: border-box; /* Asegura que el padding no incremente el ancho total */
      }

      /* 3. Ajuste (Recomendado): Ocultar el <br> que está causando un salto de línea innecesario */
      .location-container.salon-container > br {
          display: none;
      }

      /* Nota: La mayoría de los estilos (info-card, location-container, map-embed-wrapper)
        se reutilizan de las clases .location-card y .location-container de la Misa,
        asegurando uniformidad y responsividad.
      */


      /* ======================================= */
    /* == Estilos para la Sección RSVP == */
    /* ======================================= */

    /* ESTILO ESPECIAL ANIMACIÓN PARA BOTON NOMBRE */
    /* ======================================= */
    /* == Floating Label CSS == */
    /* ======================================= */
      /* ====== SECCIÓN GENERAL ====== */
.rsvp-section {
  background: linear-gradient(to bottom right, #fdf6ef, #fae3cf);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 60px 20px;
  min-height: 100vh;
}

.rsvp-container {
  background: #fff;
  border-radius: 15px;
  padding: 50px 80px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
  max-width: 700px;
  width: 100%;
}

.rsvp-title {
  text-align: center;
  color: #d51d3b;
  font-size: 2.2rem;
  margin-bottom: 40px;
  font-family: 'Poppins', sans-serif;
  letter-spacing: 0.5px;
}

/* ====== GRUPOS DE INPUT ====== */
.input-group {
  display: flex;
  align-items: center;
  border: 1.5px solid #e8a4b8;
  border-radius: 8px;
  padding: 12px 15px;
  margin-bottom: 25px;
  transition: all 0.3s ease;
  background: #fff;
}

.input-group:focus-within {
  border-color: #e91e63;
  box-shadow: 0 0 10px rgba(233, 30, 99, 0.2);
}

.input-icon {
  font-size: 1.4rem;
  margin-right: 12px;
  color: #e091a2;
}

.input-group input,
.input-group select {
  flex: 1;
  border: none;
  outline: none;
  font-size: 1rem;
  font-family: "Poppins", sans-serif;
  color: #333;
  background: transparent;
}

.input-group select {
  appearance: none;
  cursor: pointer;
}

/* ====== ETIQUETA FLOTANTE (animación Google) ====== */
.floating-label-group {
  position: relative;
  margin-bottom: 30px;
}

.floating-label-group .input-group {
  position: relative;
  z-index: 2;
}

.floating-label {
  position: absolute;
  left: 50px;
  top: 14px;
  color: #d6657b;
  font-size: 1rem;
  background: white;
  padding: 0 6px;
  pointer-events: none;
  transition: all 0.25s ease;
}

/* 🔥 EFECTO flotante: cuando escribes o haces focus */
.floating-label-group input:focus ~ .floating-label,
.floating-label-group input:not(:placeholder-shown) ~ .floating-label {
  top: -8px;
  left: 45px;
  font-size: 0.75rem;
  color: #e91e63;
  font-weight: 600;
}

/* ====== BOTÓN DE ENVÍO ====== */
.submit-btn {
  display: block;
  margin: 40px auto 0 auto;
  padding: 12px 35px;
  background: none;
  border: 2px solid #e91e63;
  color: #d61f4a;
  font-size: 1.1rem;
  letter-spacing: 1px;
  font-family: "Poppins", sans-serif;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s ease;
}

.submit-btn:hover {
  background: #e91e63;
  color: #fff;
  transform: scale(1.05);
}

.submit-arrow {
  font-size: 1.2rem;
  margin-right: 8px;
}

/* ====== EFECTO SOMBRA SUAVE ====== */
.rsvp-container:hover {
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.2);
}

/* ====== RESPONSIVE ====== */
@media (max-width: 600px) {
  .rsvp-container {
    padding: 35px 25px;
  }

  .rsvp-title {
    font-size: 1.7rem;
  }

  .floating-label {
    left: 40px;
  }
}









        /* CSS PARA FOOTER */
        /* ====== FOOTER ====== */
        .main-footer {
        width: 100%;
        margin-top: 60px;
        font-family: "Poppins", sans-serif;
        color: white;
        text-align: center;
        overflow: hidden;
        border-top: 4px solid rgba(255, 255, 255, 0.1);
        }

        /* Parte superior del footer */
        .footer-top {
        background-color: #640000; /* vino elegante */
        padding: 30px 15px;
        }

        .footer-top h4 {
        font-family: 'Great Vibes', cursive; /* tipografía elegante */
        color: #fff;
        font-size: 2.3rem;
        margin: 0;
        font-weight: 400;
        letter-spacing: 1px;
        text-shadow: 0 2px 6px rgba(0, 0, 0, 0.5);
        }

        /* Parte inferior del footer */
        .footer-bottom {
        background-color: #111;
        padding: 15px 10px;
        color: #c7c7c7;
        font-size: 0.9rem;
        border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        .footer-bottom p {
        margin: 4px 0;
        line-height: 1.4;
        }


  /* AJUSTE RESPONSIVE */
  @media (max-width: 768px) {
      .rsvp-container {
          padding: 2rem 1rem;
          width: 90%;
      }
      .rsvp-title {
          font-size: 1.5rem;
      }




       /* AJUSTE RESPONSIVE: Apilamiento en móviles */
    @media (max-width: 768px) {
        /* ... otros estilos responsivos ... */

    .papas-container-split {
        flex-direction: column; /* Apila las tarjetas de padres */
        gap: 20px;
    }
    .padrinos-card, .papas-card {
        width: 90%; /* Ancho completo en móvil */
        margin: 0 auto;
    }
}
  }










    /* ====== RESPONSIVE ====== */
    @media (max-width: 768px) {

        /* Estilos del Header */
        .hero-content-wrapper {
            flex-direction: column;
            gap: 30px;
        }

        .bloque-video, .bloque-imagen {
            width: 90%;
            max-width: 400px;
            height: auto;
            min-height: 350px;
            border-radius: 15px;
        }
        .titulo {
            font-size: 2rem;
            top: 5vh;
        }

        .papas-container-split {
            flex-direction: column; /* Apila las tarjetas de padres */                gap: 20px;
        }
        .padrinos-card, .papas-card {
              width: 90%; /* Ancho completo en móvil */
              margin: 0 auto;
        }

        .location-container {
                flex-direction: column; /* Apila las tarjetas de ubicación y mapa */
                gap: 20px;
            }
            .location-card {
                width: 90%; /* Ancho completo en móvil */
                margin: 0 auto;
            }
        }


  </style>
</head>
<body>

  <section class="hero">
    <h1 class="titulo">Celebramos el día en que dos almas se unen</h1>

    <div class="hero-content-wrapper">
        <div class="bloque-video">
          <video autoplay muted loop class="video-boda">
            <source src="multimedia/video/Video para reel de Instagram invitación de boda elegante fotográfica.mp4" type="video/mp4">
            Tu navegador no soporta videos.
          </video>
        </div>

        <div class="bloque-imagen">
          <img src="multimedia/fotos/general/imagen_presentacion.jpg" alt="Decoración" class="imagen-rosada">
        </div>
    </div>
  </section>
  <div class="separator-div"></div>

  <section class="celebration-details-section">
      <h2 class="details-title">Detalles de la Celebración</h2>
      <div class="title-underline"></div>

      <div class="main-info-box">
    <div class="info-card padrinos-card">
        <h3 class="padrinos-title">En compañía de nuestros padrinos</h3>

        <div class="padrinos-list">
            <span class="padrino-name">Alejandra Sánchez Ramírez</span>
            <span class="padrino-name">Alicia Guerrera García</span>
        </div>
    </div>

    <div class="papas-container-split">
        <div class="info-card papas-card">
            <h3>Papas de la novia</h3>
            <p class="padre-name">María Julia Flores Báez</p>
            <p class="padre-name">Augusto Lavada Juárez</p>
        </div>

          <div class="info-card papas-card">
              <h3>Papas de el novio</h3>
              <p class="padre-name">Gavina Flores García</p>
              <p class="padre-name">Hugo Arcos Rodríguez</p>
          </div>
          </div>

      </div>



      <div class="location-container">
          <div class="info-card location-card">
              <h3 class="location-title">
                  <span class="church-icon">⛪</span> MISA
              </h3>
              <div class="location-details">
                  <p>La misa será</p>
                  <p class="detail-highlight">en la capilla de la virgen de la luz</p>
                  <p>a las 3:00 pm</p>
                  <br>
                  <p class="detail-highlight">Calle 5 sur</p>
                  <p>entre 5 de mayo y 3 poniente</p>
                  <p>Tochtepec, Puebla.</p>
              </div>
          </div>

          <div class="info-card location-card map-card">
            <h3 class="location-title map-title">
                <span class="church-icon">📍</span> Ubicación de la Misa
            </h3>

            <div class="map-embed-wrapper">
                <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d839.772850898883!2d-97.82677139311464!3d18.840062966068043!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x85cf887e480a7433%3A0x546d5c8ac319cc7d!2sAyuntamiento%20de%20Tochtepec!5e1!3m2!1ses-419!2smx!4v1762615527290!5m2!1ses-419!2smx"
                        width="600"
                        height="450"
                        style="border:0;"
                        allowfullscreen=""
                        loading="lazy"
                        referrerpolicy="no-referrer-when-downgrade">
                </iframe>
          </div>
      </div>


       <div class="location-container salon-container">
          <div class="info-card salon-location-card">
              <h3 class="location-title">
                  <span class="salon-icon">🎉</span> SALÓN
              </h3>
              <div class="location-details">
                  <p>La recepción será en</p>
                  <p class="detail-highlight">"The Moon Paradise Salón"</p>
                  <p>a partir de las 6:00 pm</p>
                  <br>
                  <p class="detail-highlight">Calle 19 sur, Alhóndiga</p>
                  <p>75150, Amozoc de Hidalgo</p>
                  <p>Puebla.</p>
              </div>
          </div>
          <br>
          <div class="info-card salon-location-card map-card">
              <h3 class="location-title map-title">
                  <span class="salon-icon">📍</span> Ubicación del Salón
              </h3>

              <div class="map-embed-wrapper">
                  <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d234.03315597190522!2d-97.79910553764242!3d18.980547867900803!2m3!1f171.83303906369918!2f0!3f0!3m2!1i1024!2i768!4f35!3m3!1m2!1s0x85cf8a892183c759%3A0xabea168de6e7b857!2sThe%20Moon%20Paradise%20Salon%20de%20Eventos!5e1!3m2!1ses-419!2smx!4v1762616462263!5m2!1ses-419!2smx"
                          width=400
                          height=600
                          style="border:0;"
                          allowfullscreen=""
                          loading="lazy"
                          referrerpolicy="no-referrer-when-downgrade">
                  </iframe>
              </div>
          </div>
        </div>


  </section>


  <div class="separator-div"></div>
  
<!-- SECCCION DE FORMULARIO PARA CONFIRMACIÓN -->

  <section class="rsvp-section">
      <div class="rsvp-container">
          <h2 class="rsvp-title">Confirmar Asistencia</h2>

          <form class="rsvp-form" onsubmit="alert('Confirmación simulada enviada. Requiere backend.'); return false;">
                <div class="floating-label-group">
                    <div class="input-group">
                        <span class="input-icon">👤</span>
                        <input type="text" placeholder="Nombre" id="guest-name" required>
                    </div>
                    <label for="guest-name" class="floating-label">Nombre y apellido</label>
                </div>
              <div class="input-group">
                  <span class="input-icon">👥</span>
                  <input type="number" placeholder="Número total de invitados (Incluyéndote)" min="1" required>
              </div>
              <div class="input-group">
                  <span class="input-icon">🧸</span>
                  <input type="number" placeholder="Número de niños (menores de 12)" min="0" value="0">
              </div>
              <div class="input-group">
                  <span class="input-icon check-icon">✔️</span>
                  <select required>
                      <option value="" disabled selected>¿Asistirás?</option>
                      <option value="confirmar">Confirmar asistencia</option>
                  </select>
                  <span class="select-arrow"></span>
              </div>
              <button type="submit" class="submit-btn">
                    <span class="submit-arrow">►</span>
                    ENVIAR CONFIRMACIÓN
              </button>
            </form>
      </div>
  </section>



  <!-- FOOTER DE LA PÁGINA WEB -->
  <!-- ====== FOOTER (PIE DE PÁGINA) ====== -->
  <footer class="main-footer">
      <div class="footer-top">
          <h4>¡No podemos esperar a celebrar contigo!</h4>
      </div>
      <div class="footer-bottom">
          <p>Hecho por</p>
          <p>• J. Miguel CS</p>
      </div>
  </footer>


</body>
</html>