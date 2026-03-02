<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<title>Cowes Morning Marine Briefing</title>
<style>
  body { font-family: Arial, sans-serif; background: #eef6fc; color: #003366; padding: 20px; margin:0; }
  h1 { text-align: center; margin-bottom: 20px; }
  .card { background: #fff; padding: 20px; border-radius: 10px; margin: 15px 0; box-shadow: 0 2px 8px rgba(0,0,0,0.1); white-space: pre-line; }
</style>
</head>
<body>
<h1>Cowes Morning Marine Briefing</h1>

<div class="card">
  <h2>Weather</h2>
  <p id="temperature">Loading...</p>
  <p id="wind">Loading...</p>
  <p id="conditions">Loading...</p>
</div>

<div class="card">
  <h2>Tides</h2>
  <p id="tides">Loading...</p>
</div>

<script>
// Weather API (Open-Meteo, knots)
fetch("https://api.open-meteo.com/v1/forecast?latitude=50.763&longitude=-1.299&current_weather=true&windspeed_unit=kn")
  .then(res => res.json())
  .then(data => {
    const w = data.current_weather;
    document.getElementById('temperature').textContent = `Temperature: ${w.temperature}°C`;
    document.getElementById('wind').textContent = `Wind: ${w.windspeed} knots, direction ${w.winddirection}°`;
    document.getElementById('conditions').textContent = `Weather code: ${w.weathercode}`;
  })
  .catch(() => {
    document.getElementById('temperature').textContent = 'Weather data unavailable';
  });

// Tide info (WorldTides API demo)
fetch("https://www.worldtides.info/api/v3?extremes&lat=50.763&lon=-1.299&days=1&key=demo")
  .then(res => res.json())
  .then(data => {
    const highs = data.extremes.filter(e => e.type === "High");
    const lows = data.extremes.filter(e => e.type === "Low");
    let tidesText = '';
    highs.forEach((h,i) => {
      tidesText += `High Tide ${i+1}: ${new Date(h.date).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'})}\n`;
    });
    lows.forEach((l,i) => {
      tidesText += `Low Tide ${i+1}: ${new Date(l.date).toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'})}\n`;
    });
    document.getElementById('tides').textContent = tidesText;
  })
  .catch(() => {
    document.getElementById('tides').textContent = 'Tide data unavailable';
  });
</script>
</body>
</html>
