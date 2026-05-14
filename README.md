# Medical Assignment Optimizer (أداة توزيع تكليف الأطباء - مصر)

A comprehensive web-based platform designed to assist Egyptian medical graduates in identifying the most suitable hospital assignments based on real-world driving times and geographical proximity.

## Overview

The Medical Assignment Optimizer takes a user's starting location (either via coordinates, a Google Maps link, or browser geolocation) and calculates the driving distance and time to various medical facilities across Egypt. It provides an intuitive dashboard with interactive maps, charts, and a detailed data table to help users make informed decisions regarding their medical assignments.

## Features

- **Smart Location Input:** Accept raw coordinates (Latitude, Longitude) or parse complex Google Maps URLs (directions, places, dropped pins, etc.).
- **Automatic Geolocation:** Use the browser's built-in geolocation feature to set the starting point automatically.
- **Accurate Routing Engine:** Utilizes the OSRM (Open Source Routing Machine) API to fetch real-world driving durations and distances.
- **Interactive Visualization:**
  - **Map View:** Displays the user's origin and the top 50 closest medical facilities on a geographic map using Leaflet.js.
  - **Data Chart:** Provides a quick visual comparison of driving times to the top locations using Chart.js.
- **Coordinate Correction System:** Users can manually override and fix incorrect institution locations via a modal-based editing interface. These corrections are persistently stored in the browser's `localStorage`.
- **Excel Export:** Export the complete calculated routing data into an Excel spreadsheet (.xlsx) for offline analysis.
- **Responsive Design:** A fully responsive and modern UI featuring a tailored Arabic layout (RTL support).

## Technology Stack

- **Frontend:** HTML5, Vanilla JavaScript, CSS3
- **Mapping:** [Leaflet.js](https://leafletjs.com/) (with Carto basemaps)
- **Charts:** [Chart.js](https://www.chartjs.org/)
- **Data Export:** [SheetJS (xlsx)](https://sheetjs.com/)
- **Routing/Navigation:** OSRM (Project OSRM Table API)
- **Icons:** FontAwesome

## Project Structure

- `index.html`: The main application view containing the interface, styling, and application logic.
- `locations.json`: A static dataset file containing the names and coordinates (lat, lon) of various medical institutions in Egypt.
- `README.md`: Project documentation.

## Setup and Usage

1. **Clone or Download the Repository:** Save the project files to your local machine.
2. **Run a Local Web Server:** Due to CORS policies and fetching external JSON data, you should serve this project using a local web server rather than opening the HTML file directly.
   - Using Node.js/npx: `npx serve .`
   - Using Python 3: `python -m http.server 8000`
3. **Open the Application:** Navigate to `http://localhost:8000` (or your specific port) in your web browser.
4. **Usage:**
   - Enter your coordinates or paste a Google Maps link into the search bar, or click "تحديد الموقع الحالي تلقائياً عبر المتصفح" for auto-detection.
   - Click "بدء التحليل" to calculate the routes.
   - Wait for the OSRM engine to process the batches.
   - Review your results on the map, chart, and table. If any facility's location seems incorrect, click the edit icon to provide the correct coordinates/link.

## Note on OSRM API Limits
The application processes locations in batches of 50 to respect the OSRM public API rate limits. In production or for very large datasets, consider setting up a dedicated OSRM backend server.
