<!DOCTYPE html>
<html lang="es">
    <head>

        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Reserva de Salón - COHEP</title>
        <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
        
        <style>

            body { /*Fondo del Formulairo*/
                font-family: 'Poppins', sans-serif;
                background: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTkqfqHp71ODZcTxHm2FTtdXeu2Q3C6vgQ90Q&s'); /* Reemplaza con la URL o ruta de tu imagen */
                background-repeat: repeat; 
                background-size: auto; 
                display: flex;
                flex-direction: column;
                align-items: center;
                height: 100vh;
                margin: 5;
                color: rgb(253, 243, 43);
                text-align: center;
                overflow-x: hidden;
            }

            .navbar { /* Franja*/
                width: 100%;
                background: #FFC107;
                padding: 10px;
                text-align: center;
                box-shadow: 1px 4px 6px rgba(10, 10, 10, 100.1);
            }

            .navbar a {/* Letras de la Franja*/
                color: #000000;
                text-decoration: none;
                margin: 0 20px;
                font-size: 18px;
                font-weight: 600;
            }

            .navbar a:hover {
                text-decoration: underline;
            }

            .container {/*Formulario*/
                background: rgb(255, 255, 255, 0.1);
                padding: 15px;
                border-radius: 5px;
                box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
                width: 85%;
                max-width: 800px;            
                margin-top: 70px;
                color: black;
                text-align: center;
                backdrop-filter: blur(25px); /* Difumina el fondo */
                font-weight: 800;
            }

            h2 {
                text-align: center;
                font-weight: 600;
            }

            input, select, button, textarea {/* Tamañno y forma de los formularios*/
                width: 95%;
                padding: 10px;
                margin: 8px 0;
                border: 2px solid  #000000;
                border-radius: 10px;
                font-size: 15px;
            }

            button {
                background: #0839ea;
                color: rgb(255, 255, 255);
                border: none;
                cursor: pointer;
                font-size: 14px;
                padding: 10px;
                border-radius: 8px;
                transition: 0.5s;
                width: 200px;
                
            }

            button:hover { /*Cuando se selecciona el boton*/
                background-color: #FFC107;
                color: rgb(0, 0, 0);                
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
            
            <a href="https://docs.google.com/spreadsheets/d/e/2PACX-1vR_pZSv3gM3dYHr3o_8xzQVZUIx5qwAUdyJlELv3cIq8R5hs1Wtq6dE7ir_WThOleKlpgdxfcxdlWAZ/pubhtml">Registro de Eventos</a>
            <a href="Solicitud de Salon.html">Solicitud de Salon</a>
            
        </div>
        
        <div class="container">
            <div style="text-align: center; margin-top: 20px;">
                <img src="COHEP.png" alt="COHEP" width="300"
                alt="Abrir documento" 
                style="cursor: pointer; width: 250px;" 
                onclick="pedirClave()">            
            </div>

            <h2>Reserva de Salón</h2>

            <form id="reservaForm" method="post" action="https://script.google.com/macros/s/AKfycbzS7LaKY_rTdk-LYk5LKCQJwiUgQAg99IlIZ8mxDACtm50WcazWeNcQH-_nPp-Gs53_/exec">
                
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
                    <option value="salon_AmilcarBulnes">Salón de Convenciones Amílcar Bulnes</option>
                </select>
                
                <label for="subsalon" id="label_subsalon" style="display: none;">Seccion del Salón:</label>
                <select id="subsalon" name="subsalon" disabled>
                    <option value="" disabled selected>Secciónes del Salón de Convenciones Amílcar Bulnes</option>
                    <option value="A">Sección A</option>
                    <option value="B">Sección B</option>
                    <option value="C">Sección C: (A,B)</option>                    
                </select>
                              
                <label for="fecha">Fecha:</label>
                <input type="date" id="fecha" name="fecha_inicio" required placeholder="dd/MM/yyyy">                   
                                              
                <div style="display: flex; align-items: center; gap: 20px;">
                    <label for="hora_inicio">Hora:</label>
                    <input type="time" id="hora" name="hora_inicio" required>  
                
                    <label for="hora_final">Hora Final:</label>
                    <input type="time" id="horaf" name="hora_final" required>
                </div>
                                                                       
                <label for="participantes">Cantidad de Participantes:</label>
                <input type="number" id="participantes" name="participantes">

                <label for="tecnologia">ZOOM</label>
                <select id="tecnologia" name="tecnologia">
                    <option value="" disabled selected>Audio Visuales Requerido</option>
                    <option value="SI">Si</option>                    
                    <option value="NO">No</option>  
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
                                                       
                <button type="button" onclick="clave()">Guardar Información</button>

                                        
                <script>               
                
                    // Evento al enviar el formulario
                    document.getElementById("reservaForm").addEventListener("submit", function (event) {
                        //event.preventDefault(); // Evitar que se envíe el formulario automáticamente
                    })

                    function toggleSubSalon() {
                        let selectSalon = document.getElementById("salon_disponible");
                        let subSalon = document.getElementById("subsalon");
                        let labelSubSalon = document.getElementById("label_subsalon");

                        if (selectSalon.value === "salon_AmilcarBulnes") {
                            subSalon.disabled = false; // Habilita el select de Seccion
                            labelSubSalon.style.display = "inline"; // Muestra la etiqueta
                        } else {
                            subSalon.disabled = true; // Deshabilita el select de Seccion
                            subSalon.value = ""; // Resetea la selección
                            labelSubSalon.style.display = "none"; // Oculta la etiqueta
                        }
                    }
                    
                    /*Imagen-Base de datos*/
                    function pedirClave() {
                        var clave = prompt("Ingresa la clave para acceder:");
                        if (clave === "1234") { 
                            window.open("https://docs.google.com/spreadsheets/d/1vzbXKjf_YLEb7VSf2r0AODOjRLlvkQpHPlpB1d1z7KQ/edit?gid=0#gid=0", "_blank");
                        } else {
                            alert("Clave incorrecta. Acceso denegado.");
                        }
                    }
                                        
                    /*Boton-Enviar formulario*/                   
                    function clave() {
                        var clave = prompt("Ingresa la clave para acceder:");

                        if (clave === "1234") { 
                            alert("✅ Clave correcta. Guardando información...");
                            document.getElementById("reservaForm").submit(); 
                        } else {
                            alert("❌ Clave incorrecta. Acceso denegado.");
                        }
                    }

                </script>
                                          
            </form>           
                      
        </div>
       
    </body>
</html>
