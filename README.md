<!DOCTYPE html>
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

        </style>

    </head>
    <body>
        <link rel="icon" href="Cohep.jpg" type="image/x-icon">

        <div class="navbar">            
            <a href="https://calendar.google.com/calendar/u/0/r?pli=1">Calendario</a>
            <a href="https://docs.google.com/spreadsheets/d/e/2PACX-1vR_pZSv3gM3dYHr3o_8xzQVZUIx5qwAUdyJlELv3cIq8R5hs1Wtq6dE7ir_WThOleKlpgdxfcxdlWAZ/pubhtml">Registro de Eventos</a>
           
        </div>
        
        <div class="container">
            <div style="text-align: center; margin-top: 20px;">
                <img src="https://www.elinformativo.hn/wp-content/uploads/2018/02/Cohep.jpg" alt="COHEP" width="300">

            </div>

            <h2>Reserva de Salón</h2>

            <form id="reservaForm" method="post" action="https://script.google.com/macros/s/AKfycbybN99yto-BLZxcfLzz51IQhcZcvT5zvqWcf9fLkMJkULf8aCUJu11QxcvM72sfI9bi/exec">
                <label for="responsable">Persona Responsable:</label>
                <input type="text" id="responsable" name="encargado" required>
                
                <label for="salon">Salón Disponible:</label>
                <select id="Salón" name="salon">
                    <option value="salon1">Salón 1</option>
                    <option value="salon2">Salón 2</option>
                    <option value="salon3">Salón 3</option>
                    <option value="salon4">Salón 4</option>
                </select>
                                
                <label for="fecha">Fecha:</label>
                <input type="date" id="fecha" name="fecha_inicio" required>
                                
                <label for="hora_inicio">Hora:</label>
                <input type="time" id="hora" name="hora_inicio" required>         
                        
                <label for="participantes">Cantidad de participantes:</label>
                <input type="number" id="participantes" name="participantes" required>

                <button type="submit" >Guardar Información</button>                                
            </form>           
                      
        </div>
       
    </body>
</html>
