 <!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulario de Cotización de Seguro</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        form {
            max-width: 600px;
            margin: 0 auto;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        select, input[type="text"], input[type="email"], input[type="date"], input[type="number"] {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            margin-bottom: 20px;
        }
        .submit-btn {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            border: none;
            width: 100%;
            cursor: pointer;
        }
        .submit-btn:hover {
            background-color: #45a049;
        }
        .output {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<h1>Formulario de Cotización de Seguro de Auto</h1>

<form id="insuranceForm">
    <label for="name">Nombre y Apellido:</label>
    <input type="text" id="name" required>

    <label for="car">Año, Marca y Modelo:</label>
    <input type="text" id="car" required>

    <label for="use">Uso principal del auto:</label>
    <select id="use" required>
        <option value="Trabajo">Trabajo</option>
        <option value="Escuela">Escuela</option>
        <option value="Negocio">Negocio</option>
        <option value="Otro">Otro</option>
    </select>

    <label for="mileage">¿Cuántas millas?</label>
    <select id="mileage" required>
        <option value="5">5</option>
        <option value="10">10</option>
        <option value="15">15</option>
        <option value="20">20</option>
        <option value="25">25</option>
        <option value="30">30 o más</option>
    </select>

    <label for="lease">¿Lease?</label>
    <select id="lease" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="time">¿Cuánto tiempo llevas con el auto?</label>
    <select id="time" required>
        <option value="Menos de 6 meses">Menos de 6 meses</option>
        <option value="6 meses a 1 año">6 meses a 1 año</option>
        <option value="1 a 2 años">1 a 2 años</option>
        <option value="2 a 5 años">2 a 5 años</option>
        <option value="5 o más años">5 o más años</option>
    </select>

    <label for="uber">¿Uber o Lyft?</label>
    <select id="uber" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="insured">¿Actualmente asegurado?</label>
    <select id="insured" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="company">Compañía de Seguros / Límites:</label>
    <input type="text" id="company">

    <label for="fullCoverage">¿Full coverage?</label>
    <select id="fullCoverage" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="gender">Género:</label>
    <select id="gender" required>
        <option value="Hombre">Hombre</option>
        <option value="Mujer">Mujer</option>
    </select>

    <label for="marital">Estado Marital:</label>
    <select id="marital" required>
        <option value="Casado">Casado</option>
        <option value="Soltero">Soltero</option>
        <option value="Divorciado">Divorciado</option>
        <option value="Viudo">Viudo</option>
        <option value="Separado">Separado</option>
        <option value="Union civil">Union civil</option>
        <option value="Roommate">Roommate</option>
    </select>

    <label for="education">Nivel de educación / Ocupación:</label>
    <input type="text" id="education">

    <label for="home">¿Casa propia o rentada?</label>
    <select id="home" required>
        <option value="Propia">Propia</option>
        <option value="Rentada">Rentada</option>
    </select>

    <label for="license">Licencia:</label>
    <select id="license" required>
        <option value="Activa">Activa</option>
        <option value="Suspendida">Suspendida</option>
        <option value="Revocada">Revocada</option>
        <option value="Expirada">Expirada</option>
    </select>

    <label for="sr22">¿Requiere SR-22 o documento de responsabilidad financiera?</label>
    <select id="sr22" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="accidents">¿Accidentes con culpa en los últimos 3 años?</label>
    <select id="accidents" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="pipAccident">¿Accidente de PIP en los últimos 5 años?</label>
    <select id="pipAccident" required>
        <option value="Si">Si</option>
        <option value="No">No</option>
    </select>

    <label for="email">Email:</label>
    <input type="email" id="email" required>

    <label for="phone">Teléfono:</label>
    <input type="number" id="phone" required>

    <label for="dob">Fecha de nacimiento:</label>
    <input type="date" id="dob" required>

    <label for="address">Dirección:</label>
    <input type="text" id="address" required>

    <button type="submit" class="submit-btn">Obtener Cotización</button>
</form>

<div class="output" id="quoteResult"></div>

<script>
    document.getElementById('insuranceForm').addEventListener('submit', function(event) {
        event.preventDefault();
        // Lógica para calcular el precio según la tabla de Excel
        const countyRates = {
            "Miami-Dade": 800,
            "Broward": 750,
            "Palm Beach": 730,
            "Hillsborough": 710,
            "Orange": 690,
            "Duval": 680,
            "Collier": 660
        };

        // Obtener valores del formulario
        let county = prompt("Por favor ingresa tu condado (Miami-Dade, Broward, Palm Beach, etc.):");
        let quote = countyRates[county] || "No disponible para este condado";

        // Mostrar el resultado
        document.getElementById('quoteResult').innerHTML = `Tu cotización es: $${quote}`;
    });
</script>

</body>
</html>
