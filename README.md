# WAPP-ChartJs-workshop
## Stap 1:
Maak een Blazor WASM app aan

## Stap 2:
Maak een 'JS' folder aan voor de javascript-bestanden in 'wwwroot'

## Stap 3: 
Maak een bestand genaamd 'ChartJS.js' en plaats daarin de volgende code

```
<script>
  const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
  ];

  const data = {
    labels: labels,
    datasets: [{
      label: 'My First dataset',
      backgroundColor: 'rgb(255, 99, 132)',
      borderColor: 'rgb(255, 99, 132)',
      data: [0, 10, 5, 2, 20, 30, 45],
    }]
  };

  const config = {
    type: 'line',
    data: data,
    options: {}
  };
</script>
```

## Stap 4:
Voeg aan de index.html (Die in de wwwroot staat) het volgende script toe. `<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>`

## Stap 5:
Plaats in je Mainlayout een stuk html om de ChartJS library aan te roepen. Dit doe je zo `<canvas id="myChart"></canvas>`
