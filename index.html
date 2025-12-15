<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Project 45: 3D Capacitor Simulation</title>
    <!-- Load Plotly.js for 3D Graphing -->
    <script src="https://cdn.plot.ly/plotly-2.27.0.min.js"></script>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #1e1e1e;
            color: #ffffff;
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100vh;
        }

        header {
            text-align: center;
            padding: 20px;
            background-color: #2d2d2d;
            width: 100%;
            box-shadow: 0 4px 6px rgba(0,0,0,0.3);
            z-index: 10;
        }

        h1 { margin: 0; font-size: 1.5rem; color: #00d2ff; }
        p { margin: 5px 0 0; color: #aaa; font-size: 0.9rem; }

        #controls {
            display: flex;
            gap: 20px;
            padding: 15px;
            background: #333;
            margin-top: 10px;
            border-radius: 8px;
            align-items: center;
            flex-wrap: wrap;
            justify-content: center;
        }

        .control-group {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        label { font-size: 0.85rem; margin-bottom: 5px; color: #ccc; }

        /* Custom Button Styling */
        button {
            background-color: #00d2ff;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            color: #000;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover { background-color: #00aaff; }
        
        button.discharge {
            background-color: #ff4757;
            color: white;
        }

        /* Container for the 3D Graph */
        #plot-container {
            width: 95%;
            height: 80vh;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <header>
        <h1>Project 45: 3D Capacitor Physics</h1>
        <p>Visualizing Voltage vs. Time vs. Resistance</p>
    </header>

    <div id="controls">
        <button id="modeBtn" onclick="toggleMode()">Current Mode: CHARGING</button>
        
        <div class="control-group">
            <label for="capSlider">Capacitance: <span id="capDisplay">1000</span> µF</label>
            <input type="range" id="capSlider" min="100" max="5000" step="100" value="1000" oninput="updateSimulation()">
        </div>

        <div class="control-group">
            <label for="voltSlider">Source Voltage: <span id="voltDisplay">10</span> V</label>
            <input type="range" id="voltSlider" min="1" max="50" step="1" value="10" oninput="updateSimulation()">
        </div>
    </div>

    <div id="plot-container"></div>

    <script>
        // --- 1. CONFIGURATION STATE ---
        let isCharging = true;
        
        // --- 2. PHYSICS ENGINE ---
        function calculateData() {
            const C_microFarads = parseFloat(document.getElementById('capSlider').value);
            const Vs = parseFloat(document.getElementById('voltSlider').value);
            
            // Convert C to Farads
            const C = C_microFarads * 0.000001; 

            // Update UI Labels
            document.getElementById('capDisplay').innerText = C_microFarads;
            document.getElementById('voltDisplay').innerText = Vs;

            // Generate Axis Data
            // Time: 0 to 5 seconds
            const timePoints = 50;
            const t_values = [];
            for(let i=0; i<=timePoints; i++) t_values.push(i * (5.0/timePoints));

            // Resistance: 100 Ohms to 2000 Ohms
            const resPoints = 50;
            const r_values = [];
            for(let i=0; i<=resPoints; i++) r_values.push(100 + i * (1900/resPoints));

            // Calculate Z (Voltage) Matrix
            const z_values = [];

            for (let rIndex = 0; rIndex < r_values.length; rIndex++) {
                const R = r_values[rIndex];
                const tau = R * C; // Time Constant
                const row = [];

                for (let tIndex = 0; tIndex < t_values.length; tIndex++) {
                    const t = t_values[tIndex];
                    let voltage = 0;

                    if (isCharging) {
                        // Vc = Vs * (1 - e^(-t/RC))
                        voltage = Vs * (1 - Math.exp(-t / tau));
                    } else {
                        // Discharging: Vc = Vs * e^(-t/RC)
                        voltage = Vs * Math.exp(-t / tau);
                    }
                    row.push(voltage);
                }
                z_values.push(row);
            }

            return { t: t_values, r: r_values, z: z_values, Vs: Vs };
        }

        // --- 3. RENDERING ---
        function drawGraph() {
            const data = calculateData();

            const plotData = [{
                type: 'surface',
                x: data.t, // Time on X
                y: data.r, // Resistance on Y
                z: data.z, // Voltage on Z (Height)
                colorscale: isCharging ? 'Viridis' : 'Portland',
                contours: {
                    z: { show: true, usecolormap: true, highlightcolor: "#42f462", project: { z: true } }
                }
            }];

            const layout = {
                title: isCharging ? 'Capacitor Charging Phase' : 'Capacitor Discharging Phase',
                paper_bgcolor: '#1e1e1e', // Match body background
                plot_bgcolor: '#1e1e1e',
                font: { color: '#ffffff' },
                scene: {
                    xaxis: { title: 'Time (Seconds)', gridcolor: '#444' },
                    yaxis: { title: 'Resistance (Ohms)', gridcolor: '#444' },
                    zaxis: { title: 'Voltage (V)', range: [0, data.Vs], gridcolor: '#444' },
                    camera: {
                        eye: { x: 1.5, y: 1.5, z: 1.2 } // Initial camera angle
                    }
                },
                margin: { l: 0, r: 0, b: 0, t: 50 }
            };

            const config = { responsive: true };

            // Render Plotly Graph
            Plotly.react('plot-container', plotData, layout, config);
        }

        // --- 4. INTERACTIVITY ---
        function toggleMode() {
            isCharging = !isCharging;
            const btn = document.getElementById('modeBtn');
            
            if(isCharging) {
                btn.innerText = "Current Mode: CHARGING";
                btn.classList.remove('discharge');
            } else {
                btn.innerText = "Current Mode: DISCHARGING";
                btn.classList.add('discharge');
            }
            drawGraph();
        }

        function updateSimulation() {
            // Plotly.react is efficient for updates
            drawGraph();
        }

        // Initial Load
        drawGraph();

        // Handle Window Resize
        window.onresize = function() {
            Plotly.Plots.resize(document.getElementById('plot-container'));
        };

    </script>
</body>
</html>
