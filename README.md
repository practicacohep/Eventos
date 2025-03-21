
<html lang="es">
    <head>

        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Reserva de Salón - COHEP</title>
        <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
        
        <style>

            body {
                font-family: 'Poppins', sans-serif;
                background-color: #1471ce;
                display: flex;
                flex-direction: column;
                align-items: center;
                height: 100vh;
                margin: 5;
                color: white;
                text-align: center;
                overflow-x: hidden;
            }

            .navbar { /* Franja*/
                width: 100%;
                background: #eac508;
                padding: 10px;
                text-align: center;
                box-shadow: 1px 4px 6px rgba(10, 10, 10, 100.1);
            }

            .navbar a {/* Letras de la Franja*/
                color: #050404;
                text-decoration: none;
                margin: 0 20px;
                font-size: 18px;
                font-weight: 600;
            }

            .navbar a:hover {
                text-decoration: underline;
            }

            .container {/*Formulario*/
                background: rgb(255, 255, 255);
                padding: 20px;
                border-radius: 10px;
                box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
                width: 90%;
                max-width: 800px;            
                margin-top: 70px;
                color: black;
                text-align: center;
            }

            h2 {
                text-align: center;
                font-weight: 600;
            }

            input, select, button, textarea {/* Tamañno y forma de los formularios*/
                width: 95%;
                padding: 10px;
                margin: 10px 0;
                border: 3px solid  #FFC107;
                border-radius: 15px;
                font-size: 15px;
            }

            button {
                background-color:  #FFC107;
                color: rgb(10, 10, 10);
                border: none;
                cursor: pointer;
                font-size: 17px;
                padding: 15px;
                border-radius: 10px;
                transition: 0.3s;
            }

            button:hover {
                background-color: #4100f4;                
            }

            .franja {
                background-color: #FFC107;
                color: #1072d4;
                padding: 10px;
                font-size: 18px;
                font-weight: bold;
                text-align: justify;
                border-radius: 8px;
                margin-top: 20px;
            }

            .dropdown {
                position: relative;
                display: inline-block;
            }
                
            .dropdown-content {
                display: none;
                position: absolute;
                background-color: white;
                min-width: 200px;
                box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.2);
                padding: 10px;
                border-radius: 5px;
            }
                
            .dropdown:hover .dropdown-content {
                display: block;
            }
                
            label {
                display: block;
                cursor: pointer;
            }
                
            .selected-items {
                display: block;
                margin-top: 10px;
                font-weight: bold;
            }

        </style>

    </head>
    <body>
        <link rel="icon" href="COHEP.png" type="image/x-icon"> 
        
        <div class="navbar">            
            <a href="https://calendar.google.com/calendar/u/0/r?pli=1">Calendario</a>
            <a href="https://docs.google.com/spreadsheets/d/e/2PACX-1vR_pZSv3gM3dYHr3o_8xzQVZUIx5qwAUdyJlELv3cIq8R5hs1Wtq6dE7ir_WThOleKlpgdxfcxdlWAZ/pubhtml">Registro de Eventos</a>
           
        </div>
        
        <div class="container">
            <div style="text-align: center; margin-top: 20px;">
                <img src="COHEP.png" alt="COHEP" width="300">

            </div>

            <h2>Reserva de Salón</h2>

            <form id="reservaForm" method="post" action="https://script.google.com/macros/s/AKfycbwA1SksrlKjUd6zr5JXu6l5kpTubUZ32bfepLNhURjw8e1aFr8BbkjXcOK-Q532dQw/exec">
                <label for="responsable">Persona Responsable:</label>
                <input type="text" id="responsable" name="encargado">
                
                <label for="evento">Nombre del Evento:</label>
                <input type="text" id="evento" name="evento">

                <label for="salon">Salón Disponible:</label>
                <select id="salon_disponible" name="salon" onchange="toggleSubSalon()">
                    <option value="" disabled selected>Seleccione un salón</option>
                    <option value="Salón Albert Smith"> Salón Albert Smith</option>
                    <option value="Salón Juan Ferrera">Salón Juan Ferrera</option>
                    <option value="Salón Eduardo Facussé">Salón Eduardo Facussé</option>
                    <option value="Salón Cesar Montes"> Salón Cesar Montes</option>
                    <option value="Salón Fernando Lardizábal">Salón Fernando Lardizábal</option>
                    <option value="Sala de Prensa">Sala de Prensa</option>
                    <option value="Eventos Externos COHEP"> Eventos Externos COHEP</option>
                    <option value="salon_convenciones">Salón de Convenciones Amílcar Bulnes</option>
                </select>
                
                <label for="subsalon" id="label_subsalon" style="display: none;">Seccion del Salón:</label>
                <select id="subsalon" name="subsalon" disabled>
                    <option value="" disabled selected>Salón de Convenciones Amílcar Bulnes</option>
                    <option value="Seccion_A">Seccion A</option>
                    <option value="Seccion_B">Seccion B</option>
                    <option value="Seccion_C">Seccion C</option>                    
                </select>

                <script>
                    function toggleSubSalon() {
                        let selectSalon = document.getElementById("salon_disponible");
                        let subSalon = document.getElementById("subsalon");
                        let labelSubSalon = document.getElementById("label_subsalon");

                        if (selectSalon.value === "salon_convenciones") {
                            subSalon.disabled = false; // Habilita el select de Seccion
                            labelSubSalon.style.display = "inline"; // Muestra la etiqueta
                        } else {
                            subSalon.disabled = true; // Deshabilita el select de Seccion
                            subSalon.value = ""; // Resetea la selección
                            labelSubSalon.style.display = "none"; // Oculta la etiqueta
                        }
                    }
                </script>                
                
                <label for="fecha">Fecha:</label>
                <input type="date" id="fecha" name="fecha_inicio" required>
                                
                <label for="hora_inicio">Hora:</label>
                <input type="time" id="hora" name="hora_inicio" required>  
                
                <label for="hora_final">Hora Final:</label>
                <input type="time" id="horaf" name="hora_final" required>
                                                        
                <label for="participantes">Cantidad de participantes:</label>
                <input type="number" id="participantes" name="participantes">

                <label for="tecnologia">Tecnologia::</label>
                <select id="tecnologia" name="tecnologia">
                    <option value="" disabled selected>Audio Visuales Requerido</option>
                    <option value="Zoom"> Zoom</option>                                       
                </select>              
                        
                <label for="montaje">Montaje del Evento:</label>
                <select id="montaje" name="montaje">
                    <option value="" disabled selected>Seleccione un montaje</option>
                    <option value="Auditorio 1">Auditorio 1</option>
                    <option value="Auditorio 2">Auditorio 2</option>
                    <option value="Estilo U">Estilo U</option>
                    <option value="Mesa Redonda">Mesa Redonda</option>
                    <option value="Coctel">Coctel</option>
                    <option value="Imperial">Imperial</option>
                    <option value="Media Luna">Media Luna</option>
                    <option value="Escuela">Escuela</option>                                   
                </select>    
                
                <label for="correo">Correo Electrónico:</label>
                <input type="email" id="correo" name="correo" required placeholder="ejemplo@correo.com">

                

                         
                <button type="submit" >Guardar Información</button> 

                <p id="mensaje"></p>
                <script>
                    //Datos de ejemplo (simulación de reservas)
                    const reservas = [
                        { fecha: "2025-03-11", horaInicio: "10:00", horaFinal: "12:00", salon: "salon_convenciones", subdivision: "subsalon1" }, // A
                        { fecha: "2025-03-11", horaInicio: "14:00", horaFinal: "16:00", salon: "salon_convenciones", subdivision: "subsalon2" }, // B
                        { fecha: "2025-03-11", horaInicio: "10:00", horaFinal: "12:00", salon: "salon_convenciones", subdivision: "subsalon3" }  // C
                    ];
                
                    //Función para convertir la hora a minutos
                    function convertirAHorasMinutos(hora) {
                        const [horaParte, minutoParte] = hora.split(":").map(num => parseInt(num, 10));
                        return horaParte * 60 + minutoParte;
                    }
                
                    //Función para verificar si hay reservas en el mismo horario
                    function verificarReserva(fecha, horaInicio, horaFinal, salon, subSalon) {
                        const inicioMinutos = convertirAHorasMinutos(horaInicio);
                        const finalMinutos = convertirAHorasMinutos(horaFinal);
                
                        return reservas.some(reserva => {
                            const reservaInicio = convertirAHorasMinutos(reserva.horaInicio);
                            const reservaFinal = convertirAHorasMinutos(reserva.horaFinal);
                
                            const hayConflictoHorario = (inicioMinutos < reservaFinal && finalMinutos > reservaInicio);
                            const mismoSalon = reserva.salon === salon;
                            const mismaFecha = reserva.fecha === fecha;
                
                            // Verificar si hay conflicto con la subdivisión (si aplica)
                            const conflictoSubdivision = (subSalon === "" || reserva.subdivision === "" || subSalon === reserva.subdivision);
                
                            return mismaFecha && mismoSalon && hayConflictoHorario && conflictoSubdivision;
                        });
                    }
                
                    // Evento al enviar el formulario
                    document.getElementById("reservaForm").addEventListener("submit", function (event) {
                        event.preventDefault(); // Evitar que se envíe el formulario automáticamente
                
                        const fecha = document.getElementById("fecha").value;
                        const horaInicio = document.getElementById("hora").value;
                        const horaFinal = document.getElementById("horaf").value;
                        const salon = document.getElementById("salon_disponible").value;
                        const subSalon = document.getElementById("subsalon").value || "";  // Obtener la subdivisión si es aplicable
                        const mensaje = document.getElementById("mensaje");
                
                        // Verificar si el horario ya está reservado
                        if (verificarReserva(fecha, horaInicio, horaFinal, salon, subSalon)) {
                            mensaje.textContent = `❌ El salón "${salon}" (subdivisión ${subSalon || "general"}) ya está reservado en ese horario.`;
                            mensaje.style.color = "red";
                            return;
                        }
                
                        // Verificar si alguna sección del salón "salon_convenciones" está ocupada
                        if (salon === "salon_convenciones") {
                            const seccionOcupada = reservas.some(reserva => {
                                
                                if (reserva.fecha === fecha && reserva.salon === salon) {
                                    if (subSalon === "Seccion_A" && reserva.subdivision === "Seccion_A") {
                                        return true;
                                    }
                                    if (subSalon === "Seccion_B" && reserva.subdivision === "Seccion_B") {
                                        return true;
                                    }
                                    if (subSalon === "Seccion_C" && reserva.subdivision === "Seccion_C") {
                                        return true;
                                    }
                                }
                                return false;
                            });
                
                            if (seccionOcupada) {
                                mensaje.textContent = `❌ La sección "${subSalon}" ya está reservada en esa fecha.`;
                                mensaje.style.color = "red";
                                return;
                            }
                
                            // Verificar la lógica de restricciones entre las secciones A, B y C
                            if (subSalon === "Seccion_A") {
                                
                                if (reservas.some(r => r.fecha === fecha && r.salon === salon && r.subdivision === "Seccion_C")) {
                                    mensaje.textContent = `❌ La sección C está ocupada.`;
                                    mensaje.style.color = "red";
                                    return;
                                }
                            }
                
                            if (subSalon === "Seccion_B") {
                                
                                if (reservas.some(r => r.fecha === fecha && r.salon === salon && r.subdivision === "Seccion_C")) {
                                    mensaje.textContent = `❌ La sección C está ocupada.`;
                                    mensaje.style.color = "red";
                                    return;
                                }
                            }
                
                            if (subSalon === "Seccion_C") {

                                    if (reservas.some(r => r.fecha === fecha && r.salon === salon && r.subdivision === "Seccion_A")) {
                                    mensaje.textContent = `❌ La sección A ya está ocupada.`;
                                    mensaje.style.color = "red";
                                    return;
                                }
                                if (reservas.some(r => r.fecha === fecha && r.salon === salon && r.subdivision === "Seccion_B")) {
                                    mensaje.textContent = `❌ La sección B ya está ocupada.`;
                                    mensaje.style.color = "red";
                                    return;
                                }
                            }
                        }
                
                        // Se agrega a google sheets
                        reservas.push({ fecha, horaInicio, horaFinal, salon, subdivision: subSalon });
                
                        mensaje.textContent = `✅ ¡Reserva exitosa para "${salon}" (subdivisión ${subSalon || "general"})!`;
                        mensaje.style.color = "green";
                    
                    });
                </script>
                                          
            </form>           
                      
        </div>
       
    </body>
</html>
