# pyReality

Create mixed reality visualisations in Jupyter Notebooks

## Rapid Mixed Reality Visualisations

pyReality makes it easy to create mixed reality data visualisations in Jupyter Notebooks. It leverages the capabilities of Jupyter Notebooks to let users modify the data visualisation using their desktop computer while they view it using a head-mounted display (HMD). Currently, pyReality provides two visualisation types i.e. 3D scatterplots and 3D bar charts. More visualisations will be added later. pyReality makes it easy to rapidly create mixed reality visualisations without having to use multiple software to model and render.


## Setup pyReality

The easiest way to get started is to install the package in your Jupyter Notebook by running the following command:

```python
!pip install pyreality
```

Once installed, you can include visualisation funtions using the following command:

```python
from pyreality import pyRealityBar, pyRealityScatter, pyRealityPlot, pyRealityScatterPro
```

## Create Visualisations

With the current version of pyReality you can create the following types of visualisations:

1. 3D Bar Chart
2. 3D Scatterplot
3. Advanced 3D Scatterplot

### 3D Bar Chart

The 3D bar chart can be created using the following command:


```python
pyRealityBar(df, title, encodingX, encodingY, encodingZ, encodingColor)
```

Parameter | Description
--- | ---
df | The dataframe containing input data
title | Title for the visualisation and data visualisation
encodingX | Dictionary with field, timeUnit, type
encodingY | Dictionary with field, axis, type, numberFormat
encodingZ | Dictionary with field, type
encodingColor | Dictionary with field, type, scale, legend, numberFormat


