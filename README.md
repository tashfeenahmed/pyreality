# pyReality

Create mixed reality visualisations in Jupyter Notebooks

## Rapid Mixed Reality visualisations

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

