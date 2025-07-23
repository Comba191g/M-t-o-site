<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Radar Météo Complet</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css">
  <style>
    html, body { margin: 0; height: 100%; }
    #windy { height: 90vh; }
  </style>
</head>
<body class="bg-blue-50">
  <header class="bg-blue-800 text-white p-4 text-center text-2xl font-bold">
    Radar Météo Interactif - Pluie, Vent, Orages, Marées, Chaleur
  </header>

  <div class="flex flex-wrap justify-center gap-2 p-4 bg-white shadow">
    <button onclick="changeOverlay('rain')" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Pluie</button>
    <button onclick="changeOverlay('wind')" class="bg-green-500 hover:bg-green-700 text-white font-bold py-2 px-4 rounded">Vent</button>
    <button onclick="changeOverlay('temp')" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded">Température</button>
    <button onclick="changeOverlay('thunder')" class="bg-yellow-500 hover:bg-yellow-700 text-white font-bold py-2 px-4 rounded">Orages</button>
    <button onclick="changeOverlay('waves')" class="bg-indigo-500 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded">Vagues</button>
  </div>

  <div id="windy"></div>

  <footer class="bg-gray-200 text-center p-4 text-sm">
    Données radar par Windy.com | Marées par WorldTides.info (affiché ci-dessous)
  </footer>

  <div class="p-4">
    <h2 class="text-xl font-semibold mb-2">Infos Marées (Ajaccio, exemple)</h2>
    <iframe src="https://www.worldtides.info/widget?lat=41.9186&lon=8.7386&days=1&units=metric&color=blue" style="width:100%; height:250px; border:none;"></iframe>
  </div>

  <script src="https://unpkg.com/windy-api@latest/windy.js"></script>
  <script>
    let windyAPIInstance;

    const options = {
      key: 'PASTE_YOUR_WINDY_API_KEY_HERE', // Remplace par ta clé Windy
      lat: 41.9,
      lon: 8.7,
      zoom: 7,
      overlay: 'rain',
    };

    function changeOverlay(type) {
      if (windyAPIInstance) {
        windyAPIInstance.store.set("overlay", type);
      }
    }

    windyInit(options, windyAPI => {
      windyAPIInstance = windyAPI;
    });
  </script>
</body>
</html>
