# Watershed Delineation
A simple and efficient water delineation simulation in Python which utilizes a digital elevation machine learning model.

## What is Watershed Delineation?
**Watershed delineation** is a process for creating a boundary that represents the contributing area for a specific control point or water outlet, with the intent of characterization and analysis of portions of a study area.

## Example Usage
Example data used in this tutorial are linked below:

- Elevation: [elevation.tiff](https://pysheds.s3.us-east-2.amazonaws.com/data/elevation.tiff)
- Terrain: [impervious_area.zip](https://pysheds.s3.us-east-2.amazonaws.com/data/impervious_area.zip)
- Soil Polygons: [soils.zip](https://pysheds.s3.us-east-2.amazonaws.com/data/soils.zip)

Additional DEM datasets are available via the [USGS HydroSHEDS](https://www.hydrosheds.org/) project.

### Read DEM Data
```ruby
# Read elevation raster
# ----------------------------
from pysheds.grid import Grid

grid = Grid.from_raster('elevation.tiff')
dem = grid.read_raster('elevation.tiff')
```

Plotting Code:
```ruby
import numpy as np
import matplotlib.pyplot as plt
from matplotlib import colors
import seaborn as sns

fig, ax = plt.subplots(figsize=(8,6))
fig.patch.set_alpha(0)

plt.imshow(dem, extent=grid.extent, cmap='terrain', zorder=1)
plt.colorbar(label='Elevation (m)')
plt.grid(zorder=0)
plt.title('Digital elevation map', size=14)
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.tight_layout()
```

