<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multi-Side Grid Configuration</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            font-family: Arial, sans-serif;
        }
        .controls {
            margin-bottom: 20px;
            padding: 15px;
            background-color: #f5f5f5;
            border-radius: 5px;
        }
        .table-container {
            overflow-x: auto;
            margin-bottom: 20px;
        }
        table {
            border-collapse: collapse;
            page-break-inside: avoid;
            margin: 0 auto;
        }
        th, td {
            border: 1px solid #000;
            height: 20px;
            min-width: 15px;
            font-size: 8px;
            text-align: center;
            position: relative;
        }
        th {
            background-color: #f2f2f2;
            font-weight: bold;
        }
        .row-header {
            background-color: #f2f2f2;
            font-weight: bold;
            text-align: right;
            padding-right: 5px;
        }
        .circle {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 60%;
            height: 60%;
            border-radius: 50%;
            border: 1px solid #999;
        }
        @media print {
            @page {
                size: A4 landscape;
                margin: 0.5cm;
            }
            body {
                padding: 0;
            }
            .no-print {
                display: none;
            }
        }
        .no-print {
            margin-bottom: 20px;
        }
        button {
            padding: 8px 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            margin-right: 10px;
            margin-bottom: 10px;
        }
        button:hover {
            background-color: #45a049;
        }
        button.secondary {
            background-color: #2196F3;
        }
        button.secondary:hover {
            background-color: #0b7dda;
        }
        .config-panel {
            background-color: #fff;
            border: 1px solid #ddd;
            padding: 15px;
            margin-top: 15px;
            border-radius: 5px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }
        .side-config {
            border: 1px solid #eee;
            padding: 10px;
            border-radius: 5px;
        }
        .side-config h3 {
            margin-top: 0;
            text-align: center;
            background-color: #f0f0f0;
            padding: 5px;
            border-radius: 3px;
        }
        .config-row {
            display: flex;
            margin-bottom: 10px;
            align-items: center;
        }
        .config-row label {
            min-width: 100px;
            margin-right: 10px;
            font-size: 12px;
        }
        input[type="number"], input[type="text"] {
            width: 60px;
            padding: 5px;
            font-size: 12px;
        }
        textarea {
            width: 100%;
            height: 60px;
            font-family: monospace;
            font-size: 12px;
        }
        .gap-cell {
            background-color: #f9f9f9;
            border: none;
        }
        .side-toggle {
            display: flex;
            justify-content: center;
            margin-bottom: 15px;
        }
        .side-toggle button {
            margin: 0 5px;
            padding: 5px 10px;
            font-size: 12px;
        }
        .active-side {
            background-color: #4CAF50;
            color: white;
        }
    </style>
</head>
<body>
    <div class="no-print controls">
        <h1>Multi-Side Grid Configuration</h1>
        
        <div>
            <button onclick="window.print()">Print/Save as PDF</button>
            <button class="secondary" onclick="downloadSVG()">Download as SVG</button>
            <button onclick="applyLayout()">Apply Configuration</button>
            <button onclick="resetLayout()">Reset All</button>
        </div>
        
        <div class="side-toggle">
            <button onclick="showSide('north')" id="northBtn" class="active-side">North</button>
            <button onclick="showSide('east')" id="eastBtn">East</button>
            <button onclick="showSide('south')" id="southBtn">South</button>
            <button onclick="showSide('west')" id="westBtn">West</button>
        </div>
        
        <div class="config-panel">
            <div class="side-config" id="northConfig">
                <h3>North Side Configuration</h3>
                <div class="config-row">
                    <label for="northColumns">Columns:</label>
                    <input type="number" id="northColumns" min="1" max="100" value="64">
                </div>
                <div class="config-row">
                    <label for="northRows">Rows:</label>
                    <input type="number" id="northRows" min="1" max="100" value="5">
                </div>
                <div class="config-row">
                    <label for="northCellSize">Cell Size:</label>
                    <input type="number" id="northCellSize" min="10" max="50" value="20">
                </div>
                <div class="config-row">
                    <label for="northCircleSize">Circle Size:</label>
                    <input type="number" id="northCircleSize" min="10" max="100" value="60">
                </div>
                <div class="config-row">
                    <label for="northPattern">Row Pattern:</label>
                    <textarea id="northPattern">5</textarea>
                </div>
            </div>
            
            <div class="side-config" id="eastConfig" style="display:none">
                <h3>East Side Configuration</h3>
                <div class="config-row">
                    <label for="eastColumns">Columns:</label>
                    <input type="number" id="eastColumns" min="1" max="100" value="5">
                </div>
                <div class="config-row">
                    <label for="eastRows">Rows:</label>
                    <input type="number" id="eastRows" min="1" max="100" value="21">
                </div>
                <div class="config-row">
                    <label for="eastCellSize">Cell Size:</label>
                    <input type="number" id="eastCellSize" min="10" max="50" value="20">
                </div>
                <div class="config-row">
                    <label for="eastCircleSize">Circle Size:</label>
                    <input type="number" id="eastCircleSize" min="10" max="100" value="60">
                </div>
                <div class="config-row">
                    <label for="eastPattern">Column Pattern:</label>
                    <textarea id="eastPattern">5</textarea>
                </div>
            </div>
            
            <div class="side-config" id="southConfig" style="display:none">
                <h3>South Side Configuration</h3>
                <div class="config-row">
                    <label for="southColumns">Columns:</label>
                    <input type="number" id="southColumns" min="1" max="100" value="64">
                </div>
                <div class="config-row">
                    <label for="southRows">Rows:</label>
                    <input type="number" id="southRows" min="1" max="100" value="5">
                </div>
                <div class="config-row">
                    <label for="southCellSize">Cell Size:</label>
                    <input type="number" id="southCellSize" min="10" max="50" value="20">
                </div>
                <div class="config-row">
                    <label for="southCircleSize">Circle Size:</label>
                    <input type="number" id="southCircleSize" min="10" max="100" value="60">
                </div>
                <div class="config-row">
                    <label for="southPattern">Row Pattern:</label>
                    <textarea id="southPattern">5</textarea>
                </div>
            </div>
            
            <div class="side-config" id="westConfig" style="display:none">
                <h3>West Side Configuration</h3>
                <div class="config-row">
                    <label for="westColumns">Columns:</label>
                    <input type="number" id="westColumns" min="1" max="100" value="5">
                </div>
                <div class="config-row">
                    <label for="westRows">Rows:</label>
                    <input type="number" id="westRows" min="1" max="100" value="21">
                </div>
                <div class="config-row">
                    <label for="westCellSize">Cell Size:</label>
                    <input type="number" id="westCellSize" min="10" max="50" value="20">
                </div>
                <div class="config-row">
                    <label for="westCircleSize">Circle Size:</label>
                    <input type="number" id="westCircleSize" min="10" max="100" value="60">
                </div>
                <div class="config-row">
                    <label for="westPattern">Column Pattern:</label>
                    <textarea id="westPattern">5</textarea>
                </div>
            </div>
        </div>
    </div>

    <div class="table-container">
        <table id="gridTable">
            <tbody id="tableBody"></tbody>
        </table>
    </div>

    <script>
        // Current configuration
        let currentConfig = {
            north: { columns: 64, rows: 5, cellSize: 20, circleSize: 60, pattern: "5" },
            east: { columns: 5, rows: 21, cellSize: 20, circleSize: 60, pattern: "5" },
            south: { columns: 64, rows: 5, cellSize: 20, circleSize: 60, pattern: "5" },
            west: { columns: 5, rows: 21, cellSize: 20, circleSize: 60, pattern: "5" }
        };
        
        // DOM elements
        const tableBody = document.getElementById('tableBody');
        
        // Show selected side configuration
        function showSide(side) {
            document.querySelectorAll('.side-config').forEach(el => el.style.display = 'none');
            document.getElementById(side + 'Config').style.display = 'block';
            
            document.querySelectorAll('.side-toggle button').forEach(btn => {
                btn.classList.remove('active-side');
            });
            document.getElementById(side + 'Btn').classList.add('active-side');
        }
        
        // Apply layout based on all side configurations
        function applyLayout() {
            // Update current config from form inputs
            currentConfig = {
                north: {
                    columns: parseInt(document.getElementById('northColumns').value) || 64,
                    rows: parseInt(document.getElementById('northRows').value) || 5,
                    cellSize: parseInt(document.getElementById('northCellSize').value) || 20,
                    circleSize: parseInt(document.getElementById('northCircleSize').value) || 60,
                    pattern: document.getElementById('northPattern').value || "5"
                },
                east: {
                    columns: parseInt(document.getElementById('eastColumns').value) || 5,
                    rows: parseInt(document.getElementById('eastRows').value) || 21,
                    cellSize: parseInt(document.getElementById('eastCellSize').value) || 20,
                    circleSize: parseInt(document.getElementById('eastCircleSize').value) || 60,
                    pattern: document.getElementById('eastPattern').value || "5"
                },
                south: {
                    columns: parseInt(document.getElementById('southColumns').value) || 64,
                    rows: parseInt(document.getElementById('southRows').value) || 5,
                    cellSize: parseInt(document.getElementById('southCellSize').value) || 20,
                    circleSize: parseInt(document.getElementById('southCircleSize').value) || 60,
                    pattern: document.getElementById('southPattern').value || "5"
                },
                west: {
                    columns: parseInt(document.getElementById('westColumns').value) || 5,
                    rows: parseInt(document.getElementById('westRows').value) || 21,
                    cellSize: parseInt(document.getElementById('westCellSize').value) || 20,
                    circleSize: parseInt(document.getElementById('westCircleSize').value) || 60,
                    pattern: document.getElementById('westPattern').value || "5"
                }
            };
            
            generateCombinedGrid();
        }
        
        // Generate combined grid from all sides
        function generateCombinedGrid() {
            tableBody.innerHTML = '';
            
            // Calculate total grid dimensions
            const totalRows = currentConfig.north.rows + currentConfig.west.rows + currentConfig.south.rows;
            const totalCols = currentConfig.west.columns + currentConfig.north.columns + currentConfig.east.columns;
            
            // Create grid structure
            let grid = Array(totalRows).fill().map(() => Array(totalCols).fill(null));
            
            // Place North side (top center)
            const northStartCol = currentConfig.west.columns;
            placeSide('north', 0, northStartCol, grid);
            
            // Place West side (left)
            placeSide('west', currentConfig.north.rows, 0, grid);
            
            // Place Center area (empty or could add something)
            
            // Place East side (right)
            const eastStartCol = currentConfig.west.columns + currentConfig.north.columns;
            placeSide('east', currentConfig.north.rows, eastStartCol, grid);
            
            // Place South side (bottom center)
            const southStartRow = currentConfig.north.rows + currentConfig.west.rows;
            placeSide('south', southStartRow, northStartCol, grid
