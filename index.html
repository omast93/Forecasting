<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PeopleCert Sales Forecasting Tool</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- SheetJS (XLSX parsing library) -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Corporate Calm -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8f9fa;
        }
        .chart-container {
            position: relative;
            width: 100%;
            height: 320px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .kpi-card {
            background-color: white;
            border-radius: 0.75rem;
            padding: 1.5rem;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
            transition: transform 0.2s, box-shadow 0.2s;
            position: relative; /* Needed for tooltip positioning */
        }
        .kpi-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -2px rgb(0 0 0 / 0.1);
        }
        .control-panel-card {
            background-color: white;
            border-radius: 0.75rem;
            padding: 1.5rem;
            box-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
        }
        .toggle-label {
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0.75rem;
            border-radius: 0.5rem;
            transition: background-color 0.2s;
        }
        .toggle-label:hover {
            background-color: #f1f5f9;
        }
        .toggle-checkbox:checked + .toggle-bg {
            background-color: #2563eb;
        }
        .toggle-checkbox:checked + .toggle-bg .toggle-dot {
            transform: translateX(100%);
        }

        /* Tooltip styles */
        #kpi-tooltip {
            position: absolute;
            background-color: #333;
            color: #fff;
            padding: 0.5rem 0.75rem;
            border-radius: 0.375rem;
            font-size: 0.875rem;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.2s, visibility 0.2s;
            pointer-events: none; /* Allows clicks to pass through */
            max-width: 250px; /* Limit tooltip width */
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        #kpi-tooltip.visible {
            opacity: 1;
            visibility: visible;
        }
    </style>
</head>
<body class="text-gray-800">

    <div class="container mx-auto p-4 md:p-8">

        <header class="flex items-center justify-between mb-10">
                 <h1 class="text-3xl md:text-4xl font-bold text-gray-900 flex-grow text-center">PeopleCert Sales Forecasting Tool</h1>
            <div></div> <!-- Spacer to balance the header -->
        </header>

        <main>
            <!-- Data Upload Section (moved to the top) -->
            <section id="data-input" class="mb-12">
                <h2 class="text-2xl font-semibold mb-6 text-gray-800 border-b pb-2">Sales Data Upload</h2>
                <p class="text-gray-600 mb-4 max-w-4xl mx-auto">
                    Please upload your historical sales data as a CSV or XLSX file. Ensure the column headers are: <strong>Date,Product,Units Sold,Price,Country</strong> (or their Spanish equivalents: <strong>Fecha,Producto,Unidades Vendidas,Precio,País</strong>). This tool supports all PeopleCert products, and countries will be mapped to global regions such as North America, Latin America, Europe, Asia-Pacific, Africa, and Middle East.
                </p>
                <div class="control-panel-card p-6">
                    <div class="mt-4 flex flex-col sm:flex-row items-center gap-4">
                        <label for="csv-file-input" class="px-6 py-2 bg-blue-600 text-white font-semibold rounded-lg hover:bg-blue-700 transition shadow-md cursor-pointer">
                            Upload File
                        </label>
                        <input type="file" id="csv-file-input" accept=".csv, application/vnd.openxmlformats-officedocument.spreadsheetml.sheet, application/vnd.ms-excel" class="hidden">
                        <span id="file-name-display" class="text-gray-600 italic">No file selected</span>
                        <button id="read-calculate-btn" class="px-6 py-2 bg-purple-600 text-white font-semibold rounded-lg hover:bg-purple-700 transition shadow-md">
                            Read and Calculate
                        </button>
                    </div>
                    <div id="data-error-message" class="text-red-600 mt-2 hidden"></div>
                    <div id="file-status-message" class="text-green-600 mt-2 hidden"></div>
                </div>
            </section>

            <!-- Main Dashboard Panel -->
            <section id="dashboard" class="mb-12">
                <h2 class="text-2xl font-semibold mb-6 text-gray-800 border-b pb-2">Main Dashboard</h2>
                 <p class="text-gray-600 mb-6 max-w-4xl mx-auto">
                    This section presents an executive summary of the current situation and sales projections. You can select the year and period for which you want to generate the forecast. Key performance indicators (KPIs) and the main chart will update dynamically.
                </p>
                <div class="control-panel-card p-6 mb-8 flex flex-wrap gap-6 justify-center items-end">
                    <div>
                        <label for="forecast-year-select" class="block text-sm font-medium text-gray-700 mb-1">Forecast Year</label>
                        <select id="forecast-year-select" class="w-32 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block p-2.5"></select>
                    </div>
                    <div>
                        <label for="forecast-period-select" class="block text-sm font-medium text-gray-700 mb-1">Forecast Period</label>
                        <select id="forecast-period-select" class="w-32 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block p-2.5">
                            <option value="1H">1H</option>
                            <option value="2H">2H</option>
                            <option value="NextYear">Next Year</option>
                        </select>
                    </div>
                    <div>
                        <label for="region-filter" class="block text-sm font-medium text-gray-700 mb-1">Filter by Region</label>
                        <select id="region-filter" class="w-48 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block p-2.5">
                            <option value="All">All Regions</option>
                        </select>
                    </div>
                    <div>
                        <label for="product-filter" class="block text-sm font-medium text-gray-700 mb-1">Filter by Product</label>
                        <select id="product-filter" class="w-48 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block p-2.5">
                            <option value="All">All Products</option>
                        </select>
                    </div>
                    <!-- NEW: Country Filter -->
                    <div>
                        <label class="block text-sm font-medium text-gray-700 mb-1">Filter by Country</label>
                        <div id="country-filter-container" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block p-2.5 max-h-40 overflow-y-auto min-w-[150px]">
                            <!-- Country checkboxes will be inserted here by JS -->
                        </div>
                    </div>
                </div>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
                    <div class="kpi-card text-center" data-tooltip="Total sum of historical sales for the first half of the selected year, considering the applied filters.">
                        <h3 id="kpi-total-sales-label" class="text-gray-500 font-medium text-sm">Total Sales H1 2025</h3>
                        <p id="kpi-total-sales" class="text-3xl font-bold mt-2 text-blue-600">$0</p>
                    </div>
                    <div class="kpi-card text-center" data-tooltip="Average monthly growth rate calculated using linear regression on the historical sales of the relevant period, reflecting the trend.">
                        <h3 id="kpi-monthly-growth-label" class="text-gray-500 font-medium text-sm">Avg. Monthly Growth (2025)</h3>
                        <p id="kpi-monthly-growth" class="text-3xl font-bold mt-2 text-green-600">0%</p>
                    </div>
                    <div class="kpi-card text-center" data-tooltip="Sales projection for the future period based on the average of historical sales from the relevant period, without considering growth trends.">
                        <h3 id="kpi-forecast-linear-label" class="text-gray-500 font-medium text-sm">Projection H2 2025 (Linear)</h3>
                        <p id="kpi-forecast-linear" class="text-3xl font-bold mt-2 text-indigo-600">$0</p>
                    </div>
                    <div class="kpi-card text-center" data-tooltip="Sales projection for the future period that incorporates the growth rate calculated through linear regression and dynamically adjusts according to the activated external factors. If the value is 0, it means there is no predictable growth trend, so the linear projection should be taken as the reference.">
                        <h3 id="kpi-forecast-scenario-label" class="text-gray-500 font-medium text-sm">Projection H2 2025 (Simulated)</h3>
                        <p id="kpi-forecast-scenario" class="text-3xl font-bold mt-2 text-teal-600">$0</p>
                        <p id="kpi-forecast-scenario-percentage" class="text-lg font-semibold mt-1 text-gray-600"></p>
                    </div>
                </div>
                <div class="control-panel-card">
                    <h3 id="chart-title" class="text-xl font-semibold mb-4 text-center">Monthly Sales Evolution and Projection</h3>
                    <div class="chart-container mx-auto">
                        <canvas id="salesForecastChart"></canvas>
                    </div>
                </div>
            </section>

            <!-- Historical Analysis -->
            <section id="historical-analysis" class="mb-12">
                <h2 class="text-2xl font-semibold mb-6 text-gray-800 border-b pb-2">Historical Sales Analysis</h2>
                <p class="text-gray-600 mb-6 max-w-4xl mx-auto">
                    Explore historical sales data to better understand past performance. Use the filters to break down sales by region or product. This will help you identify which segments are most important and contextualize future projections.
                </p>
                <!-- Filters are now in the Main Dashboard Panel -->
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                    <div class="control-panel-card">
                        <h3 class="text-xl font-semibold mb-4 text-center">Sales by Region</h3>
                        <div class="chart-container mx-auto" style="max-width: 500px;">
                            <canvas id="salesByRegionChart"></canvas>
                        </div>
                    </div>
                    <div class="control-panel-card">
                        <h3 class="text-xl font-semibold mb-4 text-center">Sales by Product</h3>
                        <div class="chart-container mx-auto" style="max-width: 500px;">
                            <canvas id="salesByProductChart"></canvas>
                        </div>
                    </div>
                </div>
            </section>

            <!-- External Factors Simulator -->
            <section id="scenario-simulator" class="mb-12">
                <h2 class="text-2xl font-semibold mb-6 text-gray-800 border-b pb-2">External Factors Simulator</h2>
                <p class="text-gray-600 mb-6 max-w-4xl mx-auto">
                   This is the most interactive section of the tool. Activate or deactivate different external factors to simulate their impact on the sales forecast for the selected period. Observe how the "Simulated Projection" line on the main chart and the KPIs adjust in real-time, offering a dynamic view of potential risks and opportunities.
                </p>
                <div class="control-panel-card">
                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                        <!-- Toggles will be inserted here by JS -->
                        <div id="factors-container" class="col-span-1 md:col-span-2 lg:col-span-3 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6"></div>
                    </div>
                </div>
            </section>

            <!-- NEW: Region and Country Analysis -->
            <section id="region-country-analysis" class="mb-12">
                <h2 class="text-2xl font-semibold mb-6 text-gray-800 border-b pb-2">Region and Country Performance Analysis</h2>
                <p class="text-gray-600 mb-6 max-w-4xl mx-auto">
                    This section provides an overview of the best and worst performing regions and countries based on total sales from the uploaded data.
                </p>
                <div class="control-panel-card p-6">
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        <div>
                            <h3 class="text-xl font-semibold mb-2 text-center">Top Performing Regions</h3>
                            <ul id="top-regions-list" class="list-disc list-inside text-gray-700">
                                <!-- Populated by JS -->
                            </ul>
                        </div>
                        <div>
                            <h3 class="text-xl font-semibold mb-2 text-center">Worst Performing Regions</h3>
                            <ul id="worst-regions-list" class="list-disc list-inside text-gray-700">
                                <!-- Populated by JS -->
                            </ul>
                        </div>
                        <div>
                            <h3 class="text-xl font-semibold mb-2 text-center">Top Performing Countries</h3>
                            <ul id="top-countries-list" class="list-disc list-inside text-gray-700">
                                <!-- Populated by JS -->
                            </ul>
                        </div>
                        <div>
                            <h3 class="text-xl font-semibold mb-2 text-center">Worst Performing Countries</h3>
                            <ul id="worst-countries-list" class="list-disc list-inside text-gray-700">
                                <!-- Populated by JS -->
                            </ul>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Summary and Conclusions -->
            <section id="summary">
                <h2 class="text-2xl font-semibold mb-6 text-gray-800 border-b pb-2">Forecast Summary and Conclusions</h2>
                <div class="control-panel-card bg-blue-50 border-l-4 border-blue-500">
                     <p id="summary-text" class="text-gray-700 leading-relaxed">
                        Analysis is being calculated...
                     </p>
                     <button id="generate-strategy-btn" class="mt-4 px-6 py-2 bg-purple-600 text-white font-semibold rounded-lg hover:bg-purple-700 transition shadow-md">
                        Generate Sales Strategy ✨
                    </button>
                    <div id="strategy-output" class="mt-4 p-4 bg-purple-50 text-purple-800 rounded-lg hidden">
                        <h3 class="font-semibold mb-2">Generated Sales Strategy:</h3>
                        <p id="strategy-text" class="text-sm"></p>
                        <div id="strategy-loading" class="mt-2 text-center hidden">
                            <div class="inline-block animate-spin rounded-full h-6 w-6 border-b-2 border-purple-500"></div>
                            <p class="text-sm text-purple-600">Generating strategy...</p>
                        </div>
                    </div>
                </div>
            </section>
        </main>

        <footer class="text-center mt-12 pt-6 border-t">
            <p class="text-gray-500 text-sm">&copy; 2025 PeopleCert Forecasting Tool. All rights reserved.</p>
        </footer>

    </div>

    <script>
        // Default historical data for initial load if no data is pasted
        const defaultHistoricalDataCSV = `Date,Product,Units Sold,Price,Country
01/01/2020,ITIL,100,90,USA
01/02/2020,Prince,120,60,Canada
01/03/2020,DevOps,80,110,Mexico
01/04/2020,ITIL,110,90,USA
01/05/2020,Prince,130,60,Brazil
01/06/2020,DevOps,90,110,USA
01/07/2020,ITIL,105,92,Germany
01/08/2020,Prince,125,62,France
01/09/2020,DevOps,85,112,UK
01/10/2020,ITIL,115,92,India
01/11/2020,Prince,135,62,Japan
01/12/2020,DevOps,95,112,South Africa
01/01/2021,ITIL,110,95,USA
01/02/2021,Prince,130,65,Mexico
01/03/2021,DevOps,90,115,Canada
01/04/2021,ITIL,120,95,USA
01/05/2021,Prince,140,65,Brazil
01/06/2021,DevOps,100,115,USA
01/07/2021,ITIL,115,97,Germany
01/08/2021,Prince,135,67,France
01/09/2021,DevOps,95,117,UK
01/10/2021,ITIL,125,97,India
01/11/2021,Prince,145,67,Japan
01/12/2021,DevOps,105,117,South Africa
01/01/2022,ITIL,120,100,USA
01/02/2022,Prince,140,70,Mexico
01/03/2022,DevOps,100,120,Canada
01/04/2022,ITIL,130,100,USA
01/05/2022,Prince,150,70,Brazil
01/06/2022,DevOps,110,120,USA
01/07/2022,ITIL,125,102,Germany
01/08/2022,Prince,145,72,France
01/09/2022,DevOps,105,122,UK
01/10/2022,ITIL,135,102,India
01/11/2022,Prince,155,72,Japan
01/12/2022,DevOps,115,122,South Africa
01/01/2023,ITIL,150,100,USA
01/02/2023,Prince,200,75,USA
01/03/2023,DevOps,120,120,Canada
01/04/2023,ITIL,180,100,USA
01/05/2023,Prince,220,75,Mexico
01/06/2023,DevOps,130,120,USA
01/07/2023,ITIL,160,100,Canada
01/08/2023,Prince,210,75,USA
01/09/2023,DevOps,140,120,Mexico
01/10/2023,ITIL,190,100,USA
01/11/2023,Prince,230,75,Canada
01/12/2023,DevOps,150,120,USA
01/01/2024,ITIL,180,102,USA
01/02/2024,Prince,230,77,Mexico
01/03/2024,DevOps,140,122,Canada
01/04/2024,ITIL,200,102,USA
01/05/2024,Prince,250,77,USA
01/06/2024,DevOps,160,122,Mexico
01/07/2024,ITIL,220,105,USA
01/08/2024,Prince,270,80,Mexico
01/09/2024,DevOps,180,125,Canada
01/10/2024,ITIL,240,105,USA
01/11/2024,Prince,290,80,USA
01/12/2024,DevOps,200,125,Mexico
01/01/2025,ITIL,200,105,USA
01/02/2025,Prince,250,80,Mexico
01/03/2025,DevOps,160,125,Canada
01/04/2025,ITIL,220,105,USA
01/05/2025,Prince,270,80,USA
01/06/2025,DevOps,180,125,Mexico
01/01/2025,ITIL,100,110,Germany
01/02/2025,Prince,120,90,France
01/03/2025,DevOps,80,130,UK
01/04/2025,ITIL,110,110,India
01/05/2025,Prince,130,90,Japan
01/06/2025,DevOps,90,130,South Africa`;

        // Hardcoded external factors, bypassing CSV parsing for reliability
        let externalFactors = [
            { name: 'Global Economic Crisis', impactLevel: 5, type: 'Negative', description: 'Worldwide recession impacting general demand' },
            { name: 'Regional Pandemic', impactLevel: 5, type: 'Negative', description: 'Supply chain disruption and lockdowns' },
            { name: 'Imposed Economic Sanctions', impactLevel: 4, type: 'Negative', description: 'Trade restrictions affecting key markets' },
            { name: 'Unstable Political Situation', impactLevel: 3, type: 'Negative', description: 'Uncertainty reducing investment and consumption' },
            { name: 'LATAM Sanctions', impactLevel: 2, type: 'Negative', description: 'Trade barriers in key markets' },
            { name: 'Raw Material Cost Increase', impactLevel: 2, type: 'Negative', description: 'Reduction of margins and possible price increase' },
            { name: 'ATO Upsurge', impactLevel: 3, type: 'Positive', description: 'Significant increase in ATO performance' },
            { name: 'New Strategic Contracts', impactLevel: 4, type: 'Positive', description: 'Acquisition of important high-value clients' },
            { name: 'Future Business Opportunities', impactLevel: 2, type: 'Positive', description: 'Identification and capitalization of new market niches' },
            { name: 'EU Trade Agreement', impactLevel: 3, type: 'Positive', description: 'Opening of new market with high demand' },
            { name: 'Technological Innovation', impactLevel: 3, type: 'Positive', description: 'Launch of disruptive product' }
        ];

        // This map defines the percentage impact for each impact level (1-5)
        const impactPercentageMap = { 1: 0.03, 2: 0.07, 3: 0.12, 4: 0.18, 5: 0.25 };

        let salesData = []; // This will be populated dynamically
        let selectedForecastYear;
        let selectedForecastPeriod; // '1H', '2H', 'NextYear'
        let selectedFile = null; // Stores the file object after selection
        let selectedCountries = new Set(); // Stores currently selected countries for filtering
        
        // Expanded country to region map to cover more countries globally
        const countryToRegionMap = {
            'USA': 'North America',
            'Canada': 'North America',
            'Mexico': 'Latin America',
            'Brazil': 'Latin America',
            'Argentina': 'Latin America',
            'Colombia': 'Latin America',
            'Chile': 'Latin America',
            'Peru': 'Latin America',
            'Germany': 'Europe',
            'France': 'Europe',
            'UK': 'Europe',
            'Spain': 'Europe',
            'Italy': 'Europe',
            'Netherlands': 'Europe',
            'Belgium': 'Europe',
            'Sweden': 'Europe',
            'Norway': 'Europe',
            'Denmark': 'Europe',
            'Finland': 'Europe',
            'Ireland': 'Europe',
            'Switzerland': 'Europe',
            'Austria': 'Europe',
            'Poland': 'Europe',
            'India': 'Asia-Pacific',
            'Japan': 'Asia-Pacific',
            'China': 'Asia-Pacific',
            'Australia': 'Asia-Pacific',
            'New Zealand': 'Asia-Pacific',
            'South Korea': 'Asia-Pacific',
            'Singapore': 'Asia-Pacific',
            'Indonesia': 'Asia-Pacific',
            'Malaysia': 'Asia-Pacific',
            'Thailand': 'Asia-Pacific',
            'Philippines': 'Asia-Pacific',
            'Vietnam': 'Asia-Pacific',
            'South Africa': 'Africa',
            'Nigeria': 'Africa',
            'Egypt': 'Africa',
            'Kenya': 'Africa',
            'Morocco': 'Africa',
            'Saudi Arabia': 'Middle East',
            'UAE': 'Middle East',
            'Turkey': 'Middle East',
            // Add more countries as needed for global coverage
            'Other': 'Other' // Fallback for unmapped countries
        };

        /**
         * Cleans a header string by converting to lowercase, removing non-alphanumeric characters (except spaces),
         * normalizing spaces, and trimming. It also handles Spanish characters like 'ñ' and accents by normalizing them.
         * @param {string} header The raw header string.
         * @returns {string} The cleaned header string.
         */
        function cleanHeaderString(header) {
            // Ensure header is a string, then perform cleaning
            return String(header || '')
                                 .normalize("NFD").replace(/[\u0300-\u036f]/g, "") // Remove diacritics (e.g., é -> e, ñ -> n)
                                 .toLowerCase() 
                                 .replace(/[^a-z0-9\s]/g, '') // ONLY allow letters (a-z), numbers (0-9), and spaces.
                                 .replace(/\s+/g, ' ')       // Replace multiple spaces with a single space
                                 .trim();                    // Trim leading/trailing spaces
        }

        /**
         * Helper to determine CSV delimiter
         * @param {string} line The first line of the CSV data.
         * @returns {string} The detected delimiter (',', ';', or '\t').
         */
        function determineDelimiter(line) {
            const possibleDelimiters = [',', ';', '\t'];
            let delimiter = ',';
            let maxDelimiterCount = -1;
            possibleDelimiters.forEach(d => {
                const count = (line.match(new RegExp('\\' + d, 'g')) || []).length;
                if (count > maxDelimiterCount) {
                    maxDelimiterCount = count;
                    delimiter = d;
                }
            });
            console.log("[determineDelimiter] Detected delimiter:", JSON.stringify(delimiter)); // Log the detected delimiter
            return delimiter;
        }

        /**
         * Maps a logical header key (e.g., 'date') to its possible cleaned string variations (e.g., 'date', 'fecha').
         * This allows flexible matching against user-provided headers.
         */
        const salesHeaderKeyMap = {
            'date': ['date', 'fecha'],
            'product': ['product', 'producto'],
            'units_sold': ['units sold', 'unidades vendidas'],
            'price': ['price', 'precio'],
            'country': ['country', 'pais'] // 'país' becomes 'pais' after cleanHeaderString
        };
        
        /**
         * Helper function to get value from a row using logical header key and a specific header map.
         * @param {string} logicalHeaderKey The logical key (e.g., 'date', 'factor_name').
         * @param {Array<string>} rowValues The array of cell values for the current row.
         * @param {Map<string, number>} actualHeaderToColumnIndexMap The map of cleaned_actual_header_from_file -> column_index.
         * @param {Object} headerMap The specific headerKeyMap to use (e.g., salesHeaderKeyMap or externalFactorsHeaderKeyMap).
         * @returns {string|undefined} The value from the row, or undefined if not found.
         */
        const getValueFromRow = (logicalHeaderKey, rowValues, actualHeaderToColumnIndexMap, headerMap) => {
            const possibleCleanedHeaders = headerMap[logicalHeaderKey];
            for (const cleanedExpectedHeader of possibleCleanedHeaders) {
                const index = actualHeaderToColumnIndexMap.get(cleanedExpectedHeader);
                if (index !== undefined && index < rowValues.length) { // Ensure index is valid for rowValues
                    return rowValues[index];
                }
            }
            console.warn(`[getValueFromRow] Could not find column for logical header '${logicalHeaderKey}' (tried: ${possibleCleanedHeaders.join(', ')}).`);
            return undefined; // Not found
        };

        /**
         * Parses raw data (from CSV string or XLSX JSON) into a standardized sales data format.
         * @param {Array<Object>|string} rawData - Either a CSV string or an array of arrays from XLSX (when header:1 is used).
         * @param {string} fileType - 'csv' or 'xlsx'.
         * @returns {Array<Object>} Processed sales data.
         * @throws {Error} If data is invalid or missing required sales headers.
         */
        function processSalesData(rawData, fileType) {
            console.log(`[processSalesData] Starting for ${fileType} data...`);
            console.log(`[processSalesData] Raw data received (first 500 chars for string, or first 5 rows for array):`, 
                fileType === 'csv' ? String(rawData).substring(0, 500) : (Array.isArray(rawData) ? rawData.slice(0, 5) : rawData)); 

            const result = [];
            
            let dataRows;
            let actualHeaderToColumnIndexMap = new Map(); // Maps cleaned_actual_header_from_file -> column_index

            if (fileType === 'csv') {
                const cleanedCsv = rawData
                    .replace(/\uFEFF/g, '') // Remove BOM
                    .replace(/\r\n|\r/g, '\n') // Normalize newlines to \n
                    .replace(/[\u00A0\u2000-\u200A\u202F\u205F\u3000]/g, ' ') // Replace various unicode whitespaces
                    .trim(); 
                
                const rawLines = cleanedCsv.split('\n').filter(line => line.trim() !== '');
                if (rawLines.length < 1) {
                    throw new Error("CSV data is empty or has no headers.");
                }

                const actualHeadersRaw = rawLines[0].split(determineDelimiter(rawLines[0]));
                console.log("[processSalesData] Raw CSV headers from file:", actualHeadersRaw);

                actualHeadersRaw.forEach((header, index) => {
                    if (header !== null && header !== undefined && String(header).trim() !== '') {
                        const cleanedHeader = cleanHeaderString(header);
                        actualHeaderToColumnIndexMap.set(cleanedHeader, index);
                    } else {
                        console.warn(`[processSalesData] Skipping empty or invalid header at index ${index} in CSV file: "${header}"`);
                    }
                });
                dataRows = rawLines.slice(1);
            } else if (fileType === 'xlsx') {
                if (!Array.isArray(rawData) || rawData.length < 1) {
                    throw new Error("XLSX data is empty or malformed (expected array of arrays).");
                }
                const rawXlsxHeaders = rawData[0]; // First array is headers (due to {header: 1})
                console.log("[processSalesData] Raw XLSX headers from sheet_to_json (header:1):", rawXlsxHeaders);

                rawXlsxHeaders.forEach((header, index) => {
                    if (header !== null && header !== undefined && String(header).trim() !== '') {
                        const cleanedHeader = cleanHeaderString(header);
                        actualHeaderToColumnIndexMap.set(cleanedHeader, index);
                    } else {
                        console.warn(`[processSalesData] Skipping empty or invalid header at index ${index} in XLSX file: "${header}"`);
                    }
                });
                dataRows = rawData.slice(1);
            } else {
                throw new Error("Unsupported file type for processing.");
            }

            console.log("[processSalesData] Actual cleaned headers from file (mapped to index):", actualHeaderToColumnIndexMap);

            // Validate if all *required* logical headers are present in the actual file's headers
            const requiredLogicalHeaders = Object.keys(salesHeaderKeyMap); // Get keys from salesHeaderKeyMap
            const missingOriginalHeaders = [];

            requiredLogicalHeaders.forEach(logicalKey => {
                let found = false;
                const possibleCleanedHeaders = salesHeaderKeyMap[logicalKey];
                for (const cleanedExpectedHeader of possibleCleanedHeaders) {
                    if (actualHeaderToColumnIndexMap.has(cleanedExpectedHeader)) {
                        found = true;
                        break;
                    }
                }
                if (!found) {
                    // Report the original English name for clarity in error message
                    missingOriginalHeaders.push(salesHeaderKeyMap[logicalKey][0]); 
                }
            });
            
            if (missingOriginalHeaders.length > 0) {
                console.error("[processSalesData] Missing required headers detected:", missingOriginalHeaders);
                throw new Error(`Missing the following required headers (English or Spanish equivalent): ${missingOriginalHeaders.join(', ')}.`);
            }

            // Process data rows
            for (let i = 0; i < dataRows.length; i++) {
                const row = dataRows[i];
                let currentDataRowValues;

                if (fileType === 'csv') {
                    currentDataRowValues = row.split(determineDelimiter(row)).map(cell => cell.trim().replace(/"/g, ''));
                    if (currentDataRowValues.length < actualHeaderToColumnIndexMap.size) {
                        console.warn(`[processSalesData] Skipping malformed CSV row ${i + 1} due to insufficient columns: ${row}`);
                        continue;
                    }
                } else { // xlsx
                    currentDataRowValues = row;
                    if (!Array.isArray(currentDataRowValues) || currentDataRowValues.length < actualHeaderToColumnIndexMap.size) {
                         console.warn(`[processSalesData] Skipping malformed XLSX row ${i + 1} due to insufficient columns or not an array:`, row);
                         continue;
                    }
                }
                
                try {
                    const dateRaw = getValueFromRow('date', currentDataRowValues, actualHeaderToColumnIndexMap, salesHeaderKeyMap);
                    const product = getValueFromRow('product', currentDataRowValues, actualHeaderToColumnIndexMap, salesHeaderKeyMap);
                    const unitsRaw = getValueFromRow('units_sold', currentDataRowValues, actualHeaderToColumnIndexMap, salesHeaderKeyMap);
                    const priceRaw = getValueFromRow('price', currentDataRowValues, actualHeaderToColumnIndexMap, salesHeaderKeyMap);
                    const country = getValueFromRow('country', currentDataRowValues, actualHeaderToColumnIndexMap, salesHeaderKeyMap);

                    // Check if any critical value is undefined or empty before proceeding
                    if (dateRaw === undefined || String(dateRaw).trim() === '' ||
                        product === undefined || String(product).trim() === '' ||
                        unitsRaw === undefined || String(unitsRaw).trim() === '' ||
                        priceRaw === undefined || String(priceRaw).trim() === '' ||
                        country === undefined || String(country).trim() === '') {
                        console.warn(`[processSalesData] Skipping row ${i + 1} due to missing or empty critical data points. Row:`, row);
                        continue;
                    }

                    const dateParts = String(dateRaw).split('/');
                    let parsedDate;
                    // Try MM/DD/YYYY first (common in USA)
                    parsedDate = new Date(`${dateParts[0]}/${dateParts[1]}/${dateParts[2]}`);
                    if (isNaN(parsedDate.getTime())) { // If that fails, try DD/MM/YYYY (common in Europe/LATAM)
                        parsedDate = new Date(`${dateParts[1]}/${dateParts[0]}/${dateParts[2]}`);
                    }
                    if (isNaN(parsedDate.getTime())) {
                        throw new Error(`Invalid date format for: ${dateRaw}. Expected MM/DD/YYYY or DD/MM/YYYY.`);
                    }

                    const units = parseInt(unitsRaw);
                    const price = parseFloat(priceRaw);

                    if (isNaN(units) || isNaN(price)) {
                        throw new Error(`Invalid numeric data for Units Sold (${unitsRaw}) or Price (${priceRaw}) in row.`);
                    }

                    const countryName = String(country);
                    const region = countryToRegionMap[countryName] || 'Other';

                    result.push({
                        date: parsedDate,
                        product: product,
                        units: units,
                        price: price,
                        country: countryName,
                        region: region,
                        total: units * price
                    });
                } catch (e) {
                    console.error(`[processSalesData] Error processing row ${i + 1}:`, row, `. ${e.message}`);
                }
            }
            console.log("[processSalesData] Successfully processed", result.length, "data rows.");
            return result;
        }

        let salesForecastChart, salesByRegionChart, salesByProductChart;
        let activeFactors = new Set();
        
        const formatCurrency = (value) => {
            return new Intl.NumberFormat('en-US', { style: 'currency', currency: 'USD', minimumFractionDigits: 0 }).format(value);
        };

        const shortMonths = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

        // Helper to get monthly sales for a given year from a specific dataset
        function getMonthlySalesForYear(year, dataSet) {
            const monthlySales = {};
            for (let i = 0; i < 12; i++) {
                monthlySales[i] = 0; // Initialize all months to 0
            }
            dataSet.filter(d => d.date.getFullYear() === year)
                        .forEach(d => {
                            monthlySales[d.date.getMonth()] += d.total;
                        });
            return monthlySales;
        }

        /**
         * Calculates the monthly growth rate using simple linear regression (least squares method).
         * @param {Array<number>} values An array of sales values for consecutive months.
         * @returns {number} The monthly percentage growth rate.
         */
        function calculateTrendGrowthRate(values) {
            if (values.length < 2) {
                return 0; // Cannot calculate a trend with less than 2 data points
            }

            let sumX = 0;
            let sumY = 0;
            let sumXY = 0;
            let sumX2 = 0;
            const n = values.length;

            for (let i = 0; i < n; i++) {
                const x = i; // Month index (0, 1, 2, ...)
                const y = values[i]; // Sales value

                sumX += x;
                sumY += y;
                sumXY += (x * y);
                sumX2 += (x * x);
            }

            const denominator = (n * sumX2 - sumX * sumY);
            if (denominator === 0) {
                return 0; // Avoid division by zero, happens if all x values are the same (e.g., n=1)
            }

            const slope = (n * sumXY - sumX * sumY) / denominator;
            const averageY = sumY / n;

            if (averageY === 0) {
                return 0; // Avoid division by zero for percentage calculation
            }

            // The growth rate is the slope relative to the average sales of the period
            return slope / averageY;
        }

        // Modified to accept a specific dataset to process for forecast
        function processDataForForecast(dataToProcess) {
            console.log("[processDataForForecast] Processing data for forecast with:", dataToProcess.length, "records.");
            const allMonthlySalesByYear = {}; // { year: { monthIndex: totalSales } }
            dataToProcess.forEach(d => {
                const year = d.date.getFullYear();
                const month = d.date.getMonth();
                if (!allMonthlySalesByYear[year]) allMonthlySalesByYear[year] = {};
                if (!allMonthlySalesByYear[year][month]) allMonthlySalesByYear[year][month] = 0;
                allMonthlySalesByYear[year][month] += d.total;
            });

            let historicalValuesForGrowthCalculation = [];
            let lastMonthSalesBeforeForecast = 0;
            let totalSalesForKpi = 0;
            let kpiTotalSalesLabel = '';
            let kpiGrowthLabel = '';

            // Determine the historical period for KPI calculation based on selected forecast period
            if (selectedForecastPeriod === '1H') {
                // Forecast H1 of selectedForecastYear based on H2 of (selectedForecastYear - 1)
                const prevYear = selectedForecastYear - 1;
                const prevYearSales = allMonthlySalesByYear[prevYear] || {}; // Use allMonthlySalesByYear
                // Use H2 of previous year for growth calculation
                historicalValuesForGrowthCalculation = Object.values(prevYearSales).slice(6, 12); // Jul-Dec of previous year
                lastMonthSalesBeforeForecast = prevYearSales[11] || 0; // December of previous year

                const currentYear1HSales = allMonthlySalesByYear[selectedForecastYear] || {}; // Use allMonthlySalesByYear
                totalSalesForKpi = Object.values(currentYear1HSales).slice(0, 6).reduce((a,b) => a+b, 0);
                kpiTotalSalesLabel = `Total Sales H1 ${selectedForecastYear}`;
                kpiGrowthLabel = `Avg. Monthly Growth (H2 ${prevYear} to H1 ${selectedForecastYear})`;

            } else if (selectedForecastPeriod === '2H') {
                // Forecast H2 of selectedForecastYear based on H1 of selectedForecastYear
                const currentYearSales = allMonthlySalesByYear[selectedForecastYear] || {}; // Use allMonthlySalesByYear
                // Use H1 of current year for growth calculation
                historicalValuesForGrowthCalculation = Object.values(currentYearSales).slice(0, 6); // Jan-Jun of current year
                lastMonthSalesBeforeForecast = currentYearSales[5] || 0; // June of current year

                totalSalesForKpi = Object.values(currentYearSales).slice(0, 6).reduce((a,b) => a+b, 0);
                kpiTotalSalesLabel = `Total Sales H1 ${selectedForecastYear}`;
                kpiGrowthLabel = `Avg. Monthly Growth (H1 ${selectedForecastYear})`;

            } else if (selectedForecastPeriod === 'NextYear') {
                // Forecast NextYear (selectedForecastYear + 1) based on full selectedForecastYear
                const currentYearSales = allMonthlySalesByYear[selectedForecastYear] || {}; // Use allMonthlySalesByYear
                // Use full current year for growth calculation
                historicalValuesForGrowthCalculation = Object.values(currentYearSales); // Full current year
                lastMonthSalesBeforeForecast = currentYearSales[11] || 0; // December of current year

                totalSalesForKpi = Object.values(currentYearSales).reduce((a,b) => a+b, 0);
                kpiTotalSalesLabel = `Total Sales ${selectedForecastYear}`;
                kpiGrowthLabel = `Avg. Monthly Growth (${selectedForecastYear})`;
            }
            
            // Calculate growth rate using the new linear regression method
            const growthRate = calculateTrendGrowthRate(historicalValuesForGrowthCalculation);
            
            document.getElementById('kpi-total-sales').textContent = formatCurrency(totalSalesForKpi);
            document.getElementById('kpi-total-sales-label').textContent = kpiTotalSalesLabel;
            document.getElementById('kpi-monthly-growth').textContent = (growthRate * 100).toFixed(2) + '%';
            document.getElementById('kpi-monthly-growth-label').textContent = kpiGrowthLabel;

            return {
                historicalValuesForGrowthCalculation,
                lastMonthSalesBeforeForecast,
                growthRate,
                allMonthlySalesByYear
            };
        }

        // Modified to accept a specific dataset to calculate forecast
        function calculateForecast(dataToProcess) {
            console.log("[calculateForecast] Calculating forecast for:", dataToProcess.length, "records.");
            // Destructure historicalValuesForGrowthCalculation here
            const { historicalValuesForGrowthCalculation, lastMonthSalesBeforeForecast, growthRate, allMonthlySalesByYear } = processDataForForecast(dataToProcess);
            
            let forecastMonthsCount;
            let forecastStartMonthIndex;
            let forecastYearForLabels;
            let historicalMonthsForChart = [];
            let historicalChartLabels = [];
            let forecastOffset = 0;

            if (selectedForecastPeriod === '1H') {
                forecastMonthsCount = 6;
                forecastStartMonthIndex = 0; // Jan
                forecastYearForLabels = selectedForecastYear;
                // Historical data for chart: full previous year
                const prevYear = selectedForecastYear - 1;
                const prevYearSales = getMonthlySalesForYear(prevYear, dataToProcess);
                for (let i = 0; i < 12; i++) {
                    historicalMonthsForChart.push(prevYearSales[i] || 0);
                    historicalChartLabels.push(`${shortMonths[i]} ${prevYear}`);
                }
                forecastOffset = 12; // Forecast starts after 12 historical months
            } else if (selectedForecastPeriod === '2H') {
                forecastMonthsCount = 6;
                forecastStartMonthIndex = 6; // Jul
                forecastYearForLabels = selectedForecastYear;
                // Historical data for chart: H1 of current year
                const currentYearSales = getMonthlySalesForYear(selectedForecastYear, dataToProcess);
                for (let i = 0; i < 6; i++) {
                    historicalMonthsForChart.push(currentYearSales[i] || 0);
                    historicalChartLabels.push(`${shortMonths[i]} ${selectedForecastYear}`);
                }
                forecastOffset = 6; // Forecast starts after 6 historical months
            } else if (selectedForecastPeriod === 'NextYear') {
                forecastMonthsCount = 12;
                forecastStartMonthIndex = 0; // Jan
                forecastYearForLabels = selectedForecastYear + 1;
                // Historical data for chart: full current year
                const currentYearSales = getMonthlySalesForYear(selectedForecastYear, dataToProcess);
                for (let i = 0; i < 12; i++) {
                    historicalMonthsForChart.push(currentYearSales[i] || 0);
                    historicalChartLabels.push(`${shortMonths[i]} ${selectedForecastYear}`);
                }
                forecastOffset = 12; // Forecast starts after 12 historical months
            }

            let linearForecast = []; // This will now be the trend-based projection
            let lastValForTrend = lastMonthSalesBeforeForecast;

            for(let i=0; i < forecastMonthsCount; i++) {
                lastValForTrend *= (1 + growthRate);
                linearForecast.push(lastValForTrend); // This is the new "linear" (trend-based) forecast
            }
            
            let scenarioForecast = [...linearForecast]; // Start with the new trend-based linear forecast
            let impactMultiplier = 1.0;

            activeFactors.forEach(factorName => {
                const factor = externalFactors.find(f => f.name === factorName);
                if (factor) {
                    const impactPercent = impactPercentageMap[factor.impactLevel];
                    impactMultiplier += (factor.type === 'Positive' ? impactPercent : -impactPercent);
                }
            });
            
            scenarioForecast = scenarioForecast.map(val => val * impactMultiplier);

            // Prepare chart labels for the forecast period
            for (let i = 0; i < forecastMonthsCount; i++) {
                historicalChartLabels.push(`${shortMonths[forecastStartMonthIndex + i]} ${forecastYearForLabels}`);
            }

            return { linearForecast, scenarioForecast, chartLabels: historicalChartLabels, historicalChartData: historicalMonthsForChart, forecastOffset };
        }
        
        function updateDashboard() {
            // Only attempt to update if salesData is not empty, otherwise default values will remain
            if (salesData.length === 0) {
                console.log("[updateDashboard] salesData is empty. Resetting KPIs and charts to zero.");
                // Reset KPIs to 0 if no data is loaded
                document.getElementById('kpi-total-sales').textContent = formatCurrency(0);
                document.getElementById('kpi-monthly-growth').textContent = '0%';
                document.getElementById('kpi-forecast-linear').textContent = formatCurrency(0);
                document.getElementById('kpi-forecast-scenario').textContent = formatCurrency(0);
                document.getElementById('kpi-forecast-scenario-percentage').textContent = ''; // Clear percentage
                
                // Reset chart to empty or default state
                salesForecastChart.data.labels = [];
                salesForecastChart.data.datasets[0].data = [];
                salesForecastChart.data.datasets[1].data = [];
                salesForecastChart.data.datasets[2].data = [];
                salesForecastChart.update();

                // Note: Historical charts are updated by updateHistoricalCharts() which is called separately
                // and handles its own empty data state.

                document.getElementById('summary-text').innerHTML = "Please upload data to generate analysis.";
                return; // Exit if no data
            }
            console.log("[updateDashboard] salesData is not empty. Calculating and updating dashboard.");

            const selectedRegion = document.getElementById('region-filter').value;
            const selectedProduct = document.getElementById('product-filter').value;

            // Filter salesData based on current selections for the main forecast
            const filteredSalesDataForForecast = salesData.filter(d =>
                (selectedRegion === 'All' || d.region === selectedRegion) &&
                (selectedProduct === 'All' || d.product === selectedProduct) &&
                (selectedCountries.size === 0 || selectedCountries.has(d.country)) // Add country filter
            );

            const { linearForecast, scenarioForecast, chartLabels, historicalChartData, forecastOffset } = calculateForecast(filteredSalesDataForForecast);
            
            const totalLinear = linearForecast.reduce((a, b) => a + b, 0);
            const totalScenario = scenarioForecast.reduce((a, b) => a + b, 0);
            
            document.getElementById('kpi-forecast-linear').textContent = formatCurrency(totalLinear);
            document.getElementById('kpi-forecast-scenario').textContent = formatCurrency(totalScenario);
            
            // Calculate and display the percentage change for simulated forecast
            let scenarioPercentageText = '';
            if (totalLinear !== 0) {
                const percentageChange = ((totalScenario - totalLinear) / totalLinear) * 100;
                scenarioPercentageText = `${percentageChange >= 0 ? '+' : ''}${percentageChange.toFixed(2)}% vs Linear`;
            } else if (totalScenario > 0) {
                scenarioPercentageText = `N/A (Linear is 0, Simulated is ${formatCurrency(totalScenario)})`;
            } else {
                scenarioPercentageText = `0% vs Linear`;
            }
            document.getElementById('kpi-forecast-scenario-percentage').textContent = scenarioPercentageText;

            // Update KPI labels for forecast
            let forecastLabelPrefix = '';
            if (selectedForecastPeriod === '1H') forecastLabelPrefix = `H1 ${selectedForecastYear}`;
            else if (selectedForecastPeriod === '2H') forecastLabelPrefix = `H2 ${selectedForecastYear}`;
            else if (selectedForecastPeriod === 'NextYear') forecastLabelPrefix = `Year ${selectedForecastYear + 1}`;

            document.getElementById('kpi-forecast-linear-label').textContent = `Projection ${forecastLabelPrefix} (Linear)`;
            document.getElementById('kpi-forecast-scenario-label').textContent = `Projection ${forecastLabelPrefix} (Simulated)`;
            document.getElementById('chart-title').textContent = `Monthly Sales Evolution and Projection for ${forecastLabelPrefix}`;

            // Update chart data
            salesForecastChart.data.labels = chartLabels;
            salesForecastChart.data.datasets[0].data = historicalChartData;
            
            // Align forecast data with labels using nulls for historical period
            salesForecastChart.data.datasets[1].data = [...Array(forecastOffset).fill(null), ...linearForecast];
            salesForecastChart.data.datasets[2].data = [...Array(forecastOffset).fill(null), ...scenarioForecast];
            
            salesForecastChart.update();

            updateSummary();
            // updateHistoricalCharts() is called by updateAllChartsAndKPIs()
        }

        function initSalesForecastChart() {
            const ctx = document.getElementById('salesForecastChart').getContext('2d');
            salesForecastChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: [], // Will be populated by updateDashboard
                    datasets: [
                        {
                            label: 'Historical Sales',
                            data: [],
                            borderColor: '#3b82f6',
                            backgroundColor: 'rgba(59, 130, 246, 0.1)',
                            fill: true,
                            tension: 0.3,
                        },
                        {
                            label: 'Linear Projection',
                            data: [],
                            borderColor: '#8b5cf6',
                            borderDash: [5, 5],
                            tension: 0.3,
                        },
                        {
                            label: 'Simulated Projection',
                            data: [],
                            borderColor: '#14b8a6',
                            backgroundColor: 'rgba(20, 184, 166, 0.1)',
                            fill: true,
                            tension: 0.3,
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return formatCurrency(value);
                                }
                            }
                        }
                    }
                }
            });
        }
        
        function populateFilters() {
            console.log("[populateFilters] Populating filters based on current salesData.");
            const regionFilter = document.getElementById('region-filter');
            const productFilter = document.getElementById('product-filter');
            const forecastYearSelect = document.getElementById('forecast-year-select');
            
            // Clear previous options
            regionFilter.innerHTML = '<option value="All">All Regions</option>';
            productFilter.innerHTML = '<option value="All">All Products</option>';
            forecastYearSelect.innerHTML = ''; // Clear year options

            // Populate filters from the entire salesData (all unique values)
            const regions = [...new Set(salesData.map(d => d.region))].sort();
            const products = [...new Set(salesData.map(d => d.product))].sort();
            
            // Populate forecast year dropdown
            const currentYear = new Date().getFullYear();
            const minYearFromData = salesData.length > 0 ? Math.min(...salesData.map(d => d.date.getFullYear())) : currentYear;
            const maxYearFromData = salesData.length > 0 ? Math.max(...salesData.map(d => d.date.getFullYear())) : currentYear;

            const minAllowedYear = 2020; // Minimum year for analysis as per user request
            const maxForecastYear = 2035; // Maximum year for analysis as per user request

            const actualMinYear = Math.min(minYearFromData, minAllowedYear); 
            const actualMaxYearForDropdown = Math.max(maxYearFromData, currentYear); // Ensure current year is always an option

            for (let year = actualMinYear; year <= maxForecastYear; year++) { // Loop up to maxForecastYear
                const option = document.createElement('option');
                option.value = year;
                option.textContent = year;
                forecastYearSelect.appendChild(option);
            }
            // Set default selected year to current year if available, otherwise max year from data
            selectedForecastYear = currentYear;
            if (salesData.length > 0) {
                if (maxYearFromData >= currentYear) {
                    selectedForecastYear = maxYearFromData;
                }
            }
            // Ensure the selected year is within the allowed range and is a valid option
            if (selectedForecastYear < minAllowedYear) selectedForecastYear = minAllowedYear;
            if (selectedForecastYear > maxForecastYear) selectedForecastYear = maxForecastYear;
            forecastYearSelect.value = selectedForecastYear;

            selectedForecastPeriod = document.getElementById('forecast-period-select').value; // Get initial period

            regions.forEach(r => {
                const option = document.createElement('option');
                option.value = r;
                option.textContent = r;
                regionFilter.appendChild(option);
            });

            products.forEach(p => {
                const option = document.createElement('option');
                option.value = p;
                option.textContent = p;
                productFilter.appendChild(option);
            });
            
            // Remove existing listeners to prevent duplicates
            regionFilter.removeEventListener('change', updateAllChartsAndKPIs); // Changed to updateAllChartsAndKPIs
            productFilter.removeEventListener('change', updateAllChartsAndKPIs); // Changed to updateAllChartsAndKPIs
            forecastYearSelect.removeEventListener('change', handleForecastYearChange);
            document.getElementById('forecast-period-select').removeEventListener('change', handleForecastPeriodChange);

            // Add event listeners
            regionFilter.addEventListener('change', (event) => {
                updateAllChartsAndKPIs();
                populateCountryCheckboxes(event.target.value); // Update country checkboxes when region changes
            });
            productFilter.addEventListener('change', updateAllChartsAndKPIs); // Changed to updateAllChartsAndKPIs
            forecastYearSelect.addEventListener('change', handleForecastYearChange);
            document.getElementById('forecast-period-select').addEventListener('change', handleForecastPeriodChange);

            // Initial population of country checkboxes (for "All Regions" initially)
            populateCountryCheckboxes(regionFilter.value);
        }

        // Function to populate country checkboxes based on selected region
        function populateCountryCheckboxes(selectedRegion) {
            const countryFilterContainer = document.getElementById('country-filter-container');
            countryFilterContainer.innerHTML = ''; // Clear existing checkboxes
            selectedCountries.clear(); // Clear previously selected countries

            let countriesToDisplay = [];
            if (selectedRegion === 'All') {
                // Get all unique countries from the entire salesData
                countriesToDisplay = [...new Set(salesData.map(d => d.country))].sort();
            } else {
                // Get unique countries for the selected region
                countriesToDisplay = [...new Set(salesData.filter(d => d.region === selectedRegion).map(d => d.country))].sort();
            }

            if (countriesToDisplay.length === 0) {
                countryFilterContainer.innerHTML = '<p class="text-gray-500 text-xs text-center py-2">No countries for this region or no data.</p>';
                return;
            }

            // Add "Select All" checkbox
            const allCountriesCheckboxDiv = document.createElement('div');
            allCountriesCheckboxDiv.className = 'flex items-center mb-1';
            allCountriesCheckboxDiv.innerHTML = `
                <input type="checkbox" id="country-all" class="form-checkbox h-4 w-4 text-blue-600 rounded" checked>
                <label for="country-all" class="ml-2 text-sm text-gray-700 font-semibold">All Countries</label>
            `;
            countryFilterContainer.appendChild(allCountriesCheckboxDiv);

            // Add individual country checkboxes
            countriesToDisplay.forEach(country => {
                const countryDiv = document.createElement('div');
                countryDiv.className = 'flex items-center mb-1';
                countryDiv.innerHTML = `
                    <input type="checkbox" id="country-${country.replace(/\s+/g, '-')}" class="form-checkbox h-4 w-4 text-blue-600 rounded country-checkbox" value="${country}" checked>
                    <label for="country-${country.replace(/\s+/g, '-')}" class="ml-2 text-sm text-gray-700">${country}</label>
                `;
                countryFilterContainer.appendChild(countryDiv);
                selectedCountries.add(country); // Initially select all countries
            });

            // Event listener for "Select All"
            document.getElementById('country-all').addEventListener('change', (event) => {
                const isChecked = event.target.checked;
                document.querySelectorAll('.country-checkbox').forEach(checkbox => {
                    checkbox.checked = isChecked;
                    if (isChecked) {
                        selectedCountries.add(checkbox.value);
                    } else {
                        selectedCountries.delete(checkbox.value);
                    }
                });
                updateAllChartsAndKPIs();
            });

            // Event listeners for individual country checkboxes
            document.querySelectorAll('.country-checkbox').forEach(checkbox => {
                checkbox.addEventListener('change', (event) => {
                    if (event.target.checked) {
                        selectedCountries.add(event.target.value);
                    } else {
                        selectedCountries.delete(event.target.value);
                        // If any individual checkbox is deselected, deselect "All Countries"
                        document.getElementById('country-all').checked = false;
                    }
                    // If all individual checkboxes are selected, select "All Countries"
                    const allIndividualChecked = Array.from(document.querySelectorAll('.country-checkbox')).every(cb => cb.checked);
                    if (allIndividualChecked) {
                        document.getElementById('country-all').checked = true;
                    }
                    updateAllChartsAndKPIs();
                });
            });
        }


        function handleForecastYearChange(event) {
            selectedForecastYear = parseInt(event.target.value);
            updateAllChartsAndKPIs();
        }

        function handleForecastPeriodChange(event) {
            selectedForecastPeriod = event.target.value;
            updateAllChartsAndKPIs();
        }


        function updateHistoricalCharts() {
            console.log("[updateHistoricalCharts] Updating historical charts.");
            // These charts always use the full filtered data based on region/product filters
            if (salesData.length === 0) {
                salesByRegionChart.data.labels = [];
                salesByRegionChart.data.datasets[0].data = [];
                salesByRegionChart.update();

                salesByProductChart.data.labels = [];
                salesByProductChart.data.datasets[0].data = [];
                salesByProductChart.update();
                return;
            }

            const selectedRegion = document.getElementById('region-filter').value;
            const selectedProduct = document.getElementById('product-filter').value;

            // Filter data for historical charts based on current selections
            const filteredDataForHistorical = salesData.filter(d => 
                (selectedRegion === 'All' || d.region === selectedRegion) &&
                (selectedProduct === 'All' || d.product === selectedProduct) &&
                (selectedCountries.size === 0 || selectedCountries.has(d.country)) // Add country filter
            );

            const salesByRegion = {};
            const salesByProduct = {};

            filteredDataForHistorical.forEach(d => {
                if (!salesByRegion[d.region]) salesByRegion[d.region] = 0;
                salesByRegion[d.region] += d.total;

                if (!salesByProduct[d.product]) salesByProduct[d.product] = 0;
                salesByProduct[d.product] += d.total;
            });
            
            const regionLabels = Object.keys(salesByRegion);
            const regionValues = Object.values(salesByRegion);
            salesByRegionChart.data.labels = regionLabels;
            salesByRegionChart.data.datasets[0].data = regionValues;
            salesByRegionChart.update();

            const productLabels = Object.keys(salesByProduct);
            const productValues = Object.values(salesByProduct);
            salesByProductChart.data.labels = productLabels;
            salesByProductChart.data.datasets[0].data = productValues;
            salesByProductChart.update();
        }

        function initBarCharts() {
            const regionCtx = document.getElementById('salesByRegionChart').getContext('2d');
            salesByRegionChart = new Chart(regionCtx, {
                type: 'bar',
                data: { labels: [], datasets: [{ label: 'Total Sales', data: [], backgroundColor: '#60a5fa' }] },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false }, tooltip: { callbacks: { label: (c) => formatCurrency(c.raw) }}},
                    scales: { x: { ticks: { callback: (v) => formatCurrency(v).slice(0,-4) + 'K'}}}
                }
            });

            const productCtx = document.getElementById('salesByProductChart').getContext('2d');
            salesByProductChart = new Chart(productCtx, {
                type: 'bar',
                data: { labels: [], datasets: [{ label: 'Total Sales', data: [], backgroundColor: '#5eead4' }] },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false }, tooltip: { callbacks: { label: (c) => formatCurrency(c.raw) }}},
                    scales: {
                        y: {
                            ticks: {
                                callback: function(value, index, ticks) {
                                    const label = this.getLabelForValue(value);
                                    if (typeof label === 'string' && label.length > 15) {
                                        return label.substring(0, 15) + '...';
                                    }
                                    return label;
                                }
                            }
                        }
                    }
                }
            });

            updateHistoricalCharts(); // Initial update with potentially empty data
        }

        function createFactorToggles() {
            console.log("[createFactorToggles] Creating external factor toggles.");
            console.log("[createFactorToggles] externalFactors array content:", externalFactors);
            const container = document.getElementById('factors-container');
            container.innerHTML = ''; // Clear existing content

            if (externalFactors.length === 0) {
                console.warn("[createFactorToggles] externalFactors array is empty, no toggles will be created.");
                container.innerHTML = '<p class="text-gray-500 text-center col-span-full">No external factors defined. Please update the internal configuration.</p>';
                return;
            }

            externalFactors.forEach(factor => {
                console.log("[createFactorToggles] Processing factor:", factor.name);
                const isPositive = factor.type === 'Positive';
                const colorClass = isPositive ? 'text-green-700' : 'text-red-700';
                const impactPercentage = (impactPercentageMap[factor.impactLevel] * 100).toFixed(0); // Get percentage

                const toggleHTML = `
                    <label class="toggle-label" for="toggle-${factor.name.replace(/\s+/g, '')}">
                        <div class="flex-grow">
                            <span class="font-semibold text-gray-800">${factor.name}</span>
                            <p class="text-xs ${colorClass}">${factor.description} (${impactPercentage}% impact)</p>
                        </div>
                        <div class="relative">
                            <input type="checkbox" id="toggle-${factor.name.replace(/\s+/g, '')}" class="sr-only toggle-checkbox" data-factor-name="${factor.name}">
                            <div class="block bg-gray-200 w-10 h-6 rounded-full toggle-bg transition"></div>
                            <div class="dot absolute left-1 top-1 bg-white w-4 h-4 rounded-full transition toggle-dot"></div>
                        </div>
                    </label>
                `;
                container.innerHTML += toggleHTML;
            });

            document.querySelectorAll('.toggle-checkbox').forEach(toggle => {
                toggle.addEventListener('change', (event) => {
                    const factorName = event.target.dataset.factorName;
                    if (event.target.checked) {
                        activeFactors.add(factorName);
                    } else {
                        activeFactors.delete(factorName);
                    }
                    updateDashboard(); // Only update dashboard, historical charts don't depend on factors
                    updateSummary(); // Update summary to reflect active factors
                });
            });
        }
        
        function updateSummary() {
            console.log("[updateSummary] Updating summary text.");
            // Only update if salesData is not empty
            if (salesData.length === 0) {
                document.getElementById('summary-text').innerHTML = "Please upload data to generate analysis.";
                return;
            }

            const selectedRegion = document.getElementById('region-filter').value;
            const selectedProduct = document.getElementById('product-filter').value;
            const filteredSalesDataForForecast = salesData.filter(d =>
                (selectedRegion === 'All' || d.region === selectedRegion) &&
                (selectedProduct === 'All' || d.product === selectedProduct) &&
                (selectedCountries.size === 0 || selectedCountries.has(d.country)) // Add country filter
            );

            const { linearForecast, scenarioForecast } = calculateForecast(filteredSalesDataForForecast);
            const totalLinear = linearForecast.reduce((a, b) => a + b, 0);
            const totalScenario = scenarioForecast.reduce((a, b) => a + b, 0);
            
            let summaryText = `The base projection, maintaining a linear pace based on relevant historical performance for the selected filters, places the forecasted period's sales at <strong>${formatCurrency(totalLinear)}</strong>. `;
            
            if(activeFactors.size === 0) {
                summaryText += `The progressive growth projection, considering recent acceleration, estimates sales of <strong>${formatCurrency(totalScenario)}</strong>. This is the optimistic scenario without negative external factors.`;
            } else {
                summaryText += `Considering the selected external factors, the simulated projection adjusts to <strong>${formatCurrency(totalScenario)}</strong>. `;
                const difference = totalScenario - totalLinear;
                const percentageDiff = (totalLinear !== 0) ? (difference / totalLinear) * 100 : 0;
                
                if(difference > 0) {
                    summaryText += `This represents a potential increase of <strong>${percentageDiff.toFixed(2)}%</strong> over the linear projection. The selected positive factors are driving this growth.`;
                } else {
                    summaryText += `This represents a possible decrease of <strong>${Math.abs(percentageDiff).toFixed(2)}%</strong> compared to the linear projection. The risks activated in the simulation justify this more cautious forecast.`;
                }
                
                summaryText += "<br><br><strong>Active Factors:</strong> " + (Array.from(activeFactors).join(', ') || 'None');
            }

            document.getElementById('summary-text').innerHTML = summaryText;
        }

        async function generateSalesStrategy() {
            console.log("[generateSalesStrategy] Generating sales strategy.");
            const strategyOutputDiv = document.getElementById('strategy-output');
            const strategyTextP = document.getElementById('strategy-text');
            const strategyLoadingDiv = document.getElementById('strategy-loading');
            
            strategyOutputDiv.classList.remove('hidden');
            strategyTextP.textContent = '';
            strategyLoadingDiv.classList.remove('hidden');

            // Ensure salesData is available before generating strategy
            if (salesData.length === 0) {
                strategyTextP.textContent = "Please upload sales data before generating a strategy.";
                strategyLoadingDiv.classList.add('hidden');
                return;
            }

            const selectedRegion = document.getElementById('region-filter').value;
            const selectedProduct = document.getElementById('product-filter').value;
            const filteredSalesDataForForecast = salesData.filter(d =>
                (selectedRegion === 'All' || d.region === selectedRegion) &&
                (selectedProduct === 'All' || d.product === selectedProduct) &&
                (selectedCountries.size === 0 || selectedCountries.has(d.country)) // Add country filter
            );

            const { linearForecast, scenarioForecast } = calculateForecast(filteredSalesDataForForecast);
            const totalLinear = linearForecast.reduce((a, b) => a + b, 0);
            const totalScenario = scenarioForecast.reduce((a, b) => a + b, 0);

            const activeFactorsDescriptions = Array.from(activeFactors).map(factorName => {
                const factor = externalFactors.find(f => f.name === factorName);
                // Include impact percentage in the description for the LLM prompt
                const impactPercent = factor ? (impactPercentageMap[factor.impactLevel] * 100).toFixed(0) : 'N/A';
                return factor ? `${factor.name}: ${factor.description} (Impact: ${factor.type}, ${impactPercent}% effect)` : factorName;
            });

            // Calculate potential growth scenarios
            const currentSales = totalScenario; // Use the simulated forecast as the current sales base for strategy
            const growthScenarios = [0.10, 0.30, 0.50, 0.70, 0.90];
            let growthScenarioText = "Potential growth scenarios based on current simulated forecast:\n";
            growthScenarios.forEach(growthRate => {
                const projectedSales = currentSales * (1 + growthRate);
                growthScenarioText += `- ${ (growthRate * 100).toFixed(0)}% growth: ${formatCurrency(projectedSales)}\n`;
            });


            let prompt = `Generate a sales strategy for PeopleCert based on the following forecast data and external factors:\n\n`;
            prompt += `Forecast Period: ${selectedForecastPeriod} ${selectedForecastYear}\n`;
            prompt += `Filters: Region=${selectedRegion}, Product=${selectedProduct}\n`; // Add filters to prompt
            prompt += `Linear Projection: ${formatCurrency(totalLinear)}\n`;
            prompt += `Simulated Projection: ${formatCurrency(totalScenario)}\n`;
            prompt += `Active External Factors: ${activeFactorsDescriptions.join('; ') || 'None'}\n\n`;
            prompt += growthScenarioText; // Add growth scenarios to the prompt
            prompt += `Please provide a concise sales strategy focusing on key actions and recommendations.`;

            console.log("[generateSalesStrategy] Sending prompt to LLM:", prompt);

            try {
                let chatHistory = [];
                chatHistory.push({ role: "user", parts: [{ text: prompt }] });
                const payload = { contents: chatHistory };
                const apiKey = ""; // If you want to use models other than gemini-2.0-flash or imagen-3.0-generate-002, provide an API key here. Otherwise, leave this as-is.
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;
                
                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                
                const result = await response.json();
                console.log("[generateSalesStrategy] LLM response:", result);

                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const strategy = result.candidates[0].content.parts[0].text;
                    strategyTextP.innerHTML = strategy.replace(/\n/g, '<br>'); // Display newlines as breaks
                } else {
                    strategyTextP.textContent = "Could not generate a strategy. Please try again or adjust factors.";
                }
            } catch (error) {
                console.error("[generateSalesStrategy] Error calling Gemini API:", error);
                strategyTextP.textContent = `Error generating strategy: ${error.message}. Please check your network connection or try again.`;
            } finally {
                strategyLoadingDiv.classList.add('hidden');
            }
        }

        // Function to handle file selection (stores the file, doesn't process immediately)
        function handleFileSelection() {
            console.log("[handleFileSelection] File input change event fired."); // More explicit log
            const fileInput = document.getElementById('csv-file-input');
            const fileNameDisplay = document.getElementById('file-name-display');
            const errorMessageDiv = document.getElementById('data-error-message');
            const fileStatusMessageDiv = document.getElementById('file-status-message');

            errorMessageDiv.classList.add('hidden'); // Hide previous errors
            fileStatusMessageDiv.classList.add('hidden'); // Hide previous status messages
            fileNameDisplay.textContent = 'No file selected';
            selectedFile = null; // Reset selected file

            if (fileInput.files && fileInput.files.length > 0) { // Check for files existence
                selectedFile = fileInput.files[0];
                fileNameDisplay.textContent = selectedFile.name;
                fileStatusMessageDiv.textContent = `File "${selectedFile.name}" selected. Click 'Read and Calculate' to process.`;
                fileStatusMessageDiv.classList.remove('hidden');
                console.log("[handleFileSelection] Files in input:", fileInput.files); // Log the FileList object
                console.log("[handleFileSelection] Selected file object:", selectedFile); // Log the specific File object
            } else {
                console.log("[handleFileSelection] No file selected or files array is empty.");
                fileNameDisplay.textContent = 'No file selected';
                fileStatusMessageDiv.textContent = ''; // Clear status if no file
            }
        }

        // Function to process the selected file (triggered by button click)
        function processSelectedFile() {
            console.log("[processSelectedFile] 'Read and Calculate' button clicked.");
            const fileNameDisplay = document.getElementById('file-name-display');
            const errorMessageDiv = document.getElementById('data-error-message');
            const fileStatusMessageDiv = document.getElementById('file-status-message');

            errorMessageDiv.classList.add('hidden'); // Hide previous errors
            
            if (!selectedFile) {
                errorMessageDiv.textContent = "No file has been selected. Please select a file first.";
                errorMessageDiv.classList.remove('hidden');
                console.warn("[processSelectedFile] No file selected when 'Read and Calculate' was clicked.");
                return;
            }

            fileStatusMessageDiv.textContent = `Processing "${selectedFile.name}"...`;
            fileStatusMessageDiv.classList.remove('hidden');

            const reader = new FileReader();

            reader.onload = (e) => {
                console.log("[processSelectedFile] FileReader onload triggered. File read successfully.");
                let rawData;
                let fileType;

                if (selectedFile.name.endsWith('.csv')) {
                    rawData = e.target.result;
                    fileType = 'csv';
                    console.log("[processSelectedFile] File identified as CSV.");
                } else if (selectedFile.name.endsWith('.xlsx')) {
                    try {
                        const workbook = XLSX.read(e.target.result, { type: 'array' });
                        const firstSheetName = workbook.SheetNames[0];
                        rawData = XLSX.utils.sheet_to_json(workbook.Sheets[firstSheetName], { header: 1, raw: false });
                        fileType = 'xlsx';
                        console.log("[processSelectedFile] File identified as XLSX. First sheet name:", firstSheetName);
                    } catch (xlsxError) {
                        console.error("[processSelectedFile] Error reading XLSX file with SheetJS:", xlsxError);
                        errorMessageDiv.textContent = `Error processing XLSX file: ${xlsxError.message}. Please ensure it's a valid XLSX file with data on the first sheet.`;
                        errorMessageDiv.classList.remove('hidden');
                        fallbackToDefaultData(); // Load default data on XLSX error
                        return;
                    }
                } else {
                    errorMessageDiv.textContent = "Unsupported file type. Please upload a .csv or .xlsx file.";
                    errorMessageDiv.classList.remove('hidden');
                    fallbackToDefaultData(); // Load default data on unsupported type
                    return;
                }

                try {
                    salesData = processSalesData(rawData, fileType);
                    if (salesData.length === 0) {
                        throw new Error("No valid data could be processed from the file. Please ensure the format is correct and it contains data rows.");
                    }
                    populateFilters(); 
                    updateAllChartsAndKPIs();
                    fileStatusMessageDiv.textContent = `File "${selectedFile.name}" loaded and processed successfully.`;
                    fileStatusMessageDiv.classList.remove('hidden');
                    console.log("[processSelectedFile] Data loaded and UI updated successfully.");
                } catch (error) {
                    errorMessageDiv.textContent = `Error processing data from file: ${error.message}`;
                    errorMessageDiv.classList.remove('hidden');
                    console.error("[processSelectedFile] Error during data processing:", error);
                    fallbackToDefaultData(); // Load default data on processing error
                }
            };
            reader.onerror = () => {
                errorMessageDiv.textContent = `Error reading file: ${reader.error}`;
                errorMessageDiv.classList.remove('hidden');
                console.error("[processSelectedFile] FileReader onerror triggered:", reader.error);
                fallbackToDefaultData(); // Load default data on file read error
            };

            // Read file based on type
            if (selectedFile.name.endsWith('.csv')) {
                reader.readAsText(selectedFile);
            } else if (selectedFile.name.endsWith('.xlsx')) {
                reader.readAsArrayBuffer(selectedFile);
            }
        }

        // Function to reset UI to initial zero state
        function resetUIForNoData() {
            console.log("[resetUIForNoData] Resetting UI to initial zero state.");
            salesData = []; // Clear sales data
            
            // Reset KPIs
            document.getElementById('kpi-total-sales').textContent = formatCurrency(0);
            document.getElementById('kpi-total-sales-label').textContent = 'Total Sales H1 2025';
            document.getElementById('kpi-monthly-growth').textContent = '0%';
            document.getElementById('kpi-monthly-growth-label').textContent = 'Avg. Monthly Growth (2025)';
            document.getElementById('kpi-forecast-linear').textContent = formatCurrency(0);
            document.getElementById('kpi-forecast-scenario').textContent = formatCurrency(0);
            document.getElementById('kpi-forecast-scenario-percentage').textContent = ''; // Clear percentage
            document.getElementById('kpi-forecast-scenario-label').textContent = 'Projection H2 2025 (Simulated)';

            // Reset main chart
            if (salesForecastChart) {
                salesForecastChart.data.labels = [];
                salesForecastChart.data.datasets[0].data = [];
                salesForecastChart.data.datasets[1].data = [];
                salesForecastChart.data.datasets[2].data = [];
                salesForecastChart.update();
            }
            document.getElementById('chart-title').textContent = 'Monthly Sales Evolution and Projection';

            // Reset historical charts
            if (salesByRegionChart) {
                salesByRegionChart.data.labels = [];
                salesByRegionChart.data.datasets[0].data = [];
                salesByRegionChart.update();
            }
            if (salesByProductChart) {
                salesByProductChart.data.labels = [];
                salesByProductChart.data.datasets[0].data = [];
                salesByProductChart.update();
            }

            // Reset filters
            const regionFilter = document.getElementById('region-filter');
            const productFilter = document.getElementById('product-filter');
            const forecastYearSelect = document.getElementById('forecast-year-select');

            regionFilter.innerHTML = '<option value="All">All Regions</option>';
            productFilter.innerHTML = '<option value="All">All Products</option>';
            forecastYearSelect.innerHTML = ''; // Clear year options, will be populated by populateFilters

            // Populate year dropdown with default range
            const currentYear = new Date().getFullYear();
            const minAllowedYear = 2020;
            const maxForecastYear = 2035;
            for (let year = minAllowedYear; year <= maxForecastYear; year++) {
                const option = document.createElement('option');
                option.value = year;
                option.textContent = year;
                forecastYearSelect.appendChild(option);
            }
            forecastYearSelect.value = currentYear; // Set current year as default

            document.getElementById('summary-text').innerHTML = "Please upload data to generate analysis.";
            document.getElementById('file-name-display').textContent = 'No file selected';
            document.getElementById('data-error-message').classList.add('hidden');
            document.getElementById('file-status-message').classList.add('hidden');

            // Reset region/country analysis lists
            const topRegionsList = document.getElementById('top-regions-list');
            const worstRegionsList = document.getElementById('worst-regions-list');
            const topCountriesList = document.getElementById('top-countries-list');
            const worstCountriesList = document.getElementById('worst-countries-list');
            topRegionsList.innerHTML = '<li>No data available.</li>';
            worstRegionsList.innerHTML = '<li>No data available.</li>';
            topCountriesList.innerHTML = '<li>No data available.</li>';
            worstCountriesList.innerHTML = '<li>No data available.</li>';

            // Clear country checkboxes
            const countryFilterContainer = document.getElementById('country-filter-container');
            if (countryFilterContainer) {
                countryFilterContainer.innerHTML = '<p class="text-gray-500 text-xs text-center py-2">No countries for this region or no data.</p>';
            }
            selectedCountries.clear(); // Ensure selectedCountries is empty
        }

        // Function to load default data (used when user's file fails)
        function fallbackToDefaultData() {
            console.log("[fallbackToDefaultData] Attempting to load default historical data due to user file failure.");
            const errorMessageDiv = document.getElementById('data-error-message');
            const fileStatusMessageDiv = document.getElementById('file-status-message');
            try {
                salesData = processSalesData(defaultHistoricalDataCSV, 'csv');
                populateFilters();
                updateAllChartsAndKPIs();
                console.warn("[fallbackToDefaultData] Reverted to default historical data.");
                fileStatusMessageDiv.textContent = "Displaying default historical data (your file could not be processed).";
                fileStatusMessageDiv.classList.remove('hidden');
                // Keep errorMessageDiv visible if it was set by the file processing failure
            } catch (defaultError) {
                console.error("[fallbackToDefaultData] Failed to load default historical data:", defaultError);
                errorMessageDiv.textContent = `Failed to load default data: ${defaultError.message}. The application may not function as expected.`;
                errorMessageDiv.classList.remove('hidden'); // Ensure it's hidden if there's a new error
                fileStatusMessageDiv.classList.add('hidden'); // Hide status if default also fails
            }
        }

        // Function to update region and country performance analysis lists
        function updateRegionCountryAnalysis() {
            console.log("[updateRegionCountryAnalysis] Updating region and country performance lists.");
            const topRegionsList = document.getElementById('top-regions-list');
            const worstRegionsList = document.getElementById('worst-regions-list');
            const topCountriesList = document.getElementById('top-countries-list');
            const worstCountriesList = document.getElementById('worst-countries-list');

            // Clear previous lists
            topRegionsList.innerHTML = '';
            worstRegionsList.innerHTML = '';
            topCountriesList.innerHTML = '';
            worstCountriesList.innerHTML = '';

            if (salesData.length === 0) {
                topRegionsList.innerHTML = '<li>No data available.</li>';
                worstRegionsList.innerHTML = '<li>No data available.</li>';
                topCountriesList.innerHTML = '<li>No data available.</li>';
                worstCountriesList.innerHTML = '<li>No data available.</li>';
                return;
            }

            const salesByRegion = {};
            const salesByCountry = {};

            salesData.forEach(d => {
                if (!salesByRegion[d.region]) salesByRegion[d.region] = 0;
                salesByRegion[d.region] += d.total;

                if (!salesByCountry[d.country]) salesByCountry[d.country] = 0;
                salesByCountry[d.country] += d.total;
            });

            // Convert to array and sort for regions
            const sortedRegions = Object.entries(salesByRegion).sort(([, a], [, b]) => b - a);
            
            // Display top 3 regions
            sortedRegions.slice(0, 3).forEach(([region, sales]) => {
                const li = document.createElement('li');
                li.textContent = `${region}: ${formatCurrency(sales)}`;
                topRegionsList.appendChild(li);
            });

            // Display worst 3 regions (if more than 3)
            if (sortedRegions.length > 3) {
                sortedRegions.slice(-3).reverse().forEach(([region, sales]) => { // Reverse to show worst first
                    const li = document.createElement('li');
                    li.textContent = `${region}: ${formatCurrency(sales)}`;
                    worstRegionsList.appendChild(li);
                });
            } else if (sortedRegions.length > 0) {
                // If 3 or fewer regions, show all in top and just a message for worst
                topRegionsList.innerHTML = ''; // Clear to rebuild if needed
                sortedRegions.forEach(([region, sales]) => {
                    const li = document.createElement('li');
                    li.textContent = `${region}: ${formatCurrency(sales)}`;
                    topRegionsList.appendChild(li);
                });
                worstRegionsList.innerHTML = '<li>Not enough data for a "worst" comparison.</li>';
            }


            // Convert to array and sort for countries
            const sortedCountries = Object.entries(salesByCountry).sort(([, a], [, b]) => b - a);

            // Display top 3 countries
            sortedCountries.slice(0, 3).forEach(([country, sales]) => {
                const li = document.createElement('li');
                li.textContent = `${country}: ${formatCurrency(sales)}`;
                topCountriesList.appendChild(li);
            });

            // Display worst 3 countries (if more than 3)
            if (sortedCountries.length > 3) {
                sortedCountries.slice(-3).reverse().forEach(([country, sales]) => { // Reverse to show worst first
                    const li = document.createElement('li');
                    li.textContent = `${country}: ${formatCurrency(sales)}`;
                    worstCountriesList.appendChild(li);
                });
            } else if (sortedCountries.length > 0) {
                // If 3 or fewer countries, show all in top and just a message for worst
                topCountriesList.innerHTML = ''; // Clear to rebuild if needed
                sortedCountries.forEach(([country, sales]) => {
                    const li = document.createElement('li');
                    li.textContent = `${country}: ${formatCurrency(sales)}`;
                    topCountriesList.appendChild(li);
                });
                worstCountriesList.innerHTML = '<li>Not enough data for a "worst" comparison.</li>';
            }
        }


        function updateAllChartsAndKPIs() {
            console.log("[updateAllChartsAndKPIs] Orchestrating all UI updates based on current filters.");
            // This function now orchestrates updates based on selected year/period/region/product
            // processDataForForecast() and calculateForecast() will receive filtered data from updateDashboard()
            updateDashboard(); // Updates main chart and KPIs based on filters
            updateHistoricalCharts(); // Updates bar charts based on filters
            updateSummary(); // Updates summary text based on filters
            updateRegionCountryAnalysis(); // Updates region/country performance lists
        }

        window.onload = function() {
            console.log("[window.onload] Page fully loaded. Initializing charts and data.");
            initSalesForecastChart();
            initBarCharts();
            createFactorToggles(); // Create toggles, they will be functional but won't impact zero data
            
            // Set initial UI state to zero/empty
            resetUIForNoData();

            // Add event listener for the file input (only selects the file, doesn't process)
            document.getElementById('csv-file-input').addEventListener('change', handleFileSelection);

            // Add event listener for the new "Read and Calculate" button
            document.getElementById('read-calculate-btn').addEventListener('click', processSelectedFile);

            // Add event listener for the new sales strategy button
            document.getElementById('generate-strategy-btn').addEventListener('click', generateSalesStrategy);

            // Initial setup for filter change listeners (will be re-added in populateFilters after data load)
            // The region filter listener now also updates country checkboxes, so it's handled in populateFilters()
            document.getElementById('product-filter').addEventListener('change', updateAllChartsAndKPIs);
            document.getElementById('forecast-year-select').addEventListener('change', handleForecastYearChange);
            document.getElementById('forecast-period-select').addEventListener('change', handleForecastPeriodChange);

            // Tooltip functionality for KPI cards
            const kpiCards = document.querySelectorAll('.kpi-card');
            const tooltip = document.createElement('div');
            tooltip.id = 'kpi-tooltip';
            document.body.appendChild(tooltip);

            kpiCards.forEach(card => {
                card.addEventListener('mouseover', (event) => {
                    const tooltipText = card.dataset.tooltip;
                    if (tooltipText) {
                        tooltip.textContent = tooltipText;
                        tooltip.classList.add('visible');

                        // Position the tooltip
                        const cardRect = card.getBoundingClientRect();
                        const tooltipRect = tooltip.getBoundingClientRect();

                        // Calculate position to be above the card, centered horizontally
                        let top = cardRect.top - tooltipRect.height - 10; // 10px above the card
                        let left = cardRect.left + (cardRect.width / 2) - (tooltipRect.width / 2);

                        // Ensure tooltip stays within viewport
                        if (top < 0) { // If it goes above the top, place it below
                            top = cardRect.bottom + 10;
                        }
                        if (left < 0) { // If it goes off left, align to left edge
                            left = 0;
                        }
                        if (left + tooltipRect.width > window.innerWidth) { // If it goes off right, align to right edge
                            left = window.innerWidth - tooltipRect.width;
                        }

                        tooltip.style.top = `${top + window.scrollY}px`;
                        tooltip.style.left = `${left + window.scrollX}px`;
                    }
                });

                card.addEventListener('mouseout', () => {
                    tooltip.classList.remove('visible');
                });
            });
        };

    </script>
</body>
</html>
