[<img width="392" height="82" src="http://pyreality.co/assets/images/pyreality-logo.png" />](https://pyreality.co)

[![PyPI version](https://badge.fury.io/py/pyreality.svg)](https://badge.fury.io/py/pyreality) 

Create mixed reality visualisations in Jupyter Notebooks. Check out our [home page](https://pyreality.co) for more information.

[<img align="center" src="https://pyreality.co/assets/images/jupyter.png" />](https://pyreality.co)

## Rapid Mixed Reality Visualisations

pyReality makes it easy to create mixed reality data visualisations in Jupyter Notebooks. It leverages the capabilities of Jupyter Notebooks to let users modify the data visualisation using their desktop computer while they view it using a head-mounted display (HMD). Currently, pyReality provides two visualisation types i.e. 3D scatterplots and 3D bar charts. More visualisations will be added later. pyReality makes it easy to rapidly create mixed reality visualisations without having to use multiple software to model and render.


## Setup pyReality

The easiest way to get started is to install the package in your Jupyter Notebook by running the following command:

```python
!pip install pyreality
```

Once installed, you can include visualisation funtions using the following command:

```python
from pyreality import pyreality as pyr
```

## Create Visualisations

With the current version of pyReality you can create the following types of visualisations:

1. Immersive 3D Scatterplot
2. 3D Bar Chart
3. 3D Scatterplot

### Immersive 3D Scatterplot

The immersive scatterplot is based on BabylonJs, performant and has an immserive AR component that lets you view the data visualisation in your surroundings. The immersive scatterplot can be created using the following command:

```python
pyr.pyRealityImmersiveScatter(df, title, color, size)
```

Parameter | Description
--- | ---
df | The dataframe containing input data
title | Title for the visualisation and data visualisation
color | One of the three colors i.e. `red`, `green`, `blue`
size | You can optionally assign a size (<4). Default is 2.

Here is an example code to create a immersive scatterplot using pyReality:

```python
from pyreality import pyRealityImmersiveScatter
import pandas as pd # To open CSV

df = pd.read_csv("./yearly_data.csv") # The CSV is structured as year,t1,t2,t3,t4,t5,t6 e.g. row 1: 2017,29,29,28,27,27,26,26,26 

pyr.pyRealityImmersiveScatter(df, "Yearly Data", "red", 2)

```

### 3D Bar Chart

The 3D bar chart can be created using the following command:

```python
pyr.pyRealityBar(df, title, encodingX, encodingY, encodingZ, encodingColor)
```

Parameter | Description
--- | ---
df | The dataframe containing input data
title | Title for the visualisation and data visualisation
encodingX | Dictionary with field, timeUnit, type
encodingY | Dictionary with field, axis, type, numberFormat
encodingZ | Dictionary with field, type
encodingColor | Dictionary with field, type, scale, legend, numberFormat

Here is an example code to create a 3D bar graph using pyReality:

```python
from pyreality import pyreality as pyr
import pandas as pd # To process the data

df = pd.read_csv("./vax.csv") # The CSV is structured as Entity,Code,Day,total_vaccinations e.g. Argentina,ARG,2021-03-11,1919074
processdate = lambda dat: remLastThree(dat) # Lambda function applies to all cells in a column
cleandf = pd.DataFrame(df.Day.apply(processdate)) # .apply() the function to all cells
df['Day'] = cleandf['Day']
df = df.groupby(['Day','Code','Entity'],as_index=False).agg({'total_vaccinations': 'sum'})
dfUK = df[df.Entity == 'United Kingdom']
dfUS = df[df.Entity == 'United States']
dfGermany = df[df.Entity == 'Germany']
dfFrance = df[df.Entity == 'France']
dfSweden = df[df.Entity == 'Sweden']
dfCountries = pd.concat([dfUK, dfUS, dfSweden, dfFrance, dfGermany], ignore_index=True, sort=False)
dfCountries.columns = ['Month', 'Code', 'Country', 'Vaccinations']
del dfCountries['Code']

encodingX = {
    "field": "Month",
    "timeUnit": "month",
    "type": "temporal"
}

encodingY = {
    "field": "Vaccinations",
    "type": "quantitative",
    "axis": {
        "face": "back"
    },
    "numberFormat": ",.2r"
}
encodingZ = {
    "field": "Country",
    "type": "nominal"
}
encodingColor = {
    "field": "Vaccinations",
    "type": "quantitative",
    "scale": {
        "scheme": "interpolateInferno"
    },
    "legend": {
        "orient": "left"
    },
    "numberFormat": ",.2r"
}

pyr.pyRealityBar(dfCountries, "Vaccinations", encodingX, encodingY, encodingZ, encodingColor)

```

### 3D Scatterplot

The 3D scatterplot can be created using the following command:


```python
pyr.pyRealityScatter(df, title, encodingX, encodingY, encodingZ, encodingColor)
```

Parameter | Description
--- | ---
df | The dataframe containing input data
title | Title for the visualisation and data visualisation
encodingX | Dictionary with field, timeUnit, type
encodingY | Dictionary with field, axis, type, numberFormat
encodingZ | Dictionary with field, type
encodingColor | Dictionary with field, type, scale, legend, numberFormat

Here is an example code to create a 3D bar graph using pyReality:

```python
from pyreality import pyreality as pyr
import pandas as pd # To process the data

df = pd.read_csv("./vax.csv") # The CSV is structured as Entity,Code,Day,total_vaccinations e.g. Argentina,ARG,2021-03-11,1919074
processdate = lambda dat: remLastThree(dat) # Lambda function applies to all cells in a column
cleandf = pd.DataFrame(df.Day.apply(processdate)) # .apply() the function to all cells
df['Day'] = cleandf['Day']
df = df.groupby(['Day','Code','Entity'],as_index=False).agg({'total_vaccinations': 'sum'})
dfUK = df[df.Entity == 'United Kingdom']
dfUS = df[df.Entity == 'United States']
dfGermany = df[df.Entity == 'Germany']
dfFrance = df[df.Entity == 'France']
dfSweden = df[df.Entity == 'Sweden']
dfCountries = pd.concat([dfUK, dfUS, dfSweden, dfFrance, dfGermany], ignore_index=True, sort=False)
dfCountries.columns = ['Month', 'Code', 'Country', 'Vaccinations']
del dfCountries['Code']

encodingX = {
    "field": "Month",
    "timeUnit": "month",
    "type": "temporal"
}

encodingY = {
    "field": "Vaccinations",
    "type": "quantitative",
    "axis": {
        "face": "back"
    },
    "numberFormat": ",.2r"
}
encodingZ = {
    "field": "Country",
    "type": "nominal"
}
encodingColor = {
    "field": "Vaccinations",
    "type": "quantitative",
    "scale": {
        "scheme": "interpolateInferno"
    },
    "legend": {
        "orient": "left"
    },
    "numberFormat": ",.2r"
}

pyr.pyRealityScatter(dfCountries, "Vaccinations", encodingX, encodingY, encodingZ, encodingColor)

```

## Team
pyReality is in ongoing development by the Design Informatics Group at the University of Edinburgh, UK, led by [Dr Benjamin Bach](https://visualinteractivedata.github.io/), [Dr Bettina Nissen](http://data-things.com/) and [Tashfeen Ahmed](https://tashfeen.me).

## License

MIT © Copyright 2021 [Dr Benjamin Bach](https://visualinteractivedata.github.io/), [Dr Bettina Nissen](http://data-things.com/) and [Tashfeen Ahmed](https://tashfeen.me) - University of Edinburgh, UK (Design Informatics Group) - All rights reserved
