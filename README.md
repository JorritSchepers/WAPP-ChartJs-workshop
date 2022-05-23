# WAPP-ChartJs-workshop
In deze workshop voegen we twee charts toe aan een blazor webpage: Een Pie Chart en een Line Chart. Eerst maken we een Pie Chart. 

## 1. Setup

### 1.1 Stap 1: Repo
Clone de repo.

### 1.2 Stap 2: NuGet package
Voeg de volgende NuGet package toe: `ChartJs.Blazor.Fork (version 2.0.2)`

### 1.3 Stap 3: Import
Voeg de volgende 2 regels toe aan `wwwroot/index.html`.

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@2.9.4/dist/Chart.min.js"></script>
<script src="_content/ChartJs.Blazor.Fork/ChartJsBlazorInterop.js"></script>
```

## 2. Pie Chart

### 2.1 Stap 4: \<Chart>
Voeg het volgende stuk code onder de header: Pie Chart in `Pages/index.razor`

```html 
<Chart Config="_configPie"></Chart>
```

### 2.2 Stap 5: Config
Initializeer `_configPie` bovenaan het code block.

#### 2.3.1 Stap 5.1
```cs
private PieConfig _configPie;
```

En declareer deze vervolgens in de `OnInitialized()` methode.

#### 2.3.2 Stap 5.2
```cs
_configPie = new PieConfig
{
    Options = new PieOptions
    {
        Responsive = true,
    }
};
```

### 2.4 Stap 6: labels
Voeg de labels aan de config toe als volgt. Dit moet ook in de `OnInitialized()` methode.
```cs
foreach (string label in _labels)
{
    _configPie.Data.Labels.Add(label);
}
```

### 2.5 Stap 7: Data set
Als laatste voeg je de data set toe. 

```cs
PieDataset<int> dataset = new PieDataset<int>(_data)
{
    BackgroundColor = new[]
    {
        ColorUtil.ColorHexString(255, 99, 132),
        ColorUtil.ColorHexString(255, 205, 86),
        ColorUtil.ColorHexString(75, 192, 192),
        ColorUtil.ColorHexString(54, 162, 235),
    }
};

_configPie.Data.Datasets.Add(dataset);
```

## 2. Line Chart
Probeer nu een line chart te maken met de volgende stukken code.

```html
<Chart Config="_configLine"></Chart>
```

```cs
private LineConfig _configLine;  
```

```cs
_configLine = new LineConfig()
{
    Options = new LineOptions()
    {
        Responsive = true,
    }
};
```
 
```cs
foreach (int x in new int[] {1,2,3,4})
{
    _configLine.Data.Labels.Add("" + x);
}

```
 
```cs
LineDataset<int> datasetLine = new LineDataset<int>(_data)
{
    BackgroundColor = ColorUtil.ColorHexString(255, 99, 132),
    // Met de Line tenstion kan je spelen door de lijn strakker te tekenen of heel los. Probeer maar LineTension = 2 te doen :)
    // LineTension = 0.1
};

_configLine.Data.Datasets.Add(datasetLine);
```

## 3. Extra 
Als je de chart kleiner wilt maken kun je er een `<div>` omheen wrappen en daarin met css de breedte te veranderen. In de css (`wwwroot/css/app.css`) is er een class aangemaakt genaamd `chart` met daarin `width: 50%;`. Hieronder is een voorbeeld te zien:
```html
<div class="chart">
  <Chart Config="_configLine"></Chart>
</div>
```