# FOUNDeRY Case Study

Using all or part of the [cover type](https://archive.ics.uci.edu/ml/datasets/Covertype) data set build a multi-class classification model for predicting types of forest cover from the input data available.

# Project Structure

This project is structured as follows:

- foundery-case-study/
  - [data](./data/)
  - [img](./img/)
  - [case-study.ipynb](./case-study.ipynb)
  - [Pipfile](./Pipfile)
  - [Pipfile.lock](./Pipfile.lock)
  - [README.md](./README.md)

This project makes use of pipenv to manage dependencies and virtual environments. All data is stored in the data subfolder however the raw data files are excluded from the repository. The data required in this project is downloaded in the [case-study notebook](./case-study.ipynb).

# Getting Started

To get started just clone the repository and install the project dependencies with pipenv. If you don't already have pipenv installed check out the [official docs](https://docs.pipenv.org/) for details on installation.

```bash
$ git clone https://github.com/BradleyKirton/foundery-case-study
$ cd foundery-case-study
$ pipenv install
$ pipenv shell
$ jupyter lab
```

## Project Dependencies

Outside of the Python standard library this project requires the following libraries:

- [jupyterlab](https://jupyter.org/)
- [requests](http://docs.python-requests.org/en/master/)
- [pandas](https://pandas.pydata.org/)
- [scikit-learn](http://scikit-learn.org/stable/index.html)
- [scipy](https://www.scipy.org/)
- [altair](https://altair-viz.github.io/)
- [matplotlib](https://matplotlib.org/)
- [tqdm](https://tqdm.github.io/)

For a detailed dependency graph run the following command.

```bash
pipenv graph
```

# Case Study Overview

### Data Set Information

>	Predicting forest cover type from cartographic variables only
	(no remotely sensed data).  The actual forest cover type for
	a given observation (30 x 30 meter cell) was determined from
	US Forest Service (USFS) Region 2 Resource Information System 
	(RIS) data.  Independent variables were derived from data
	originally obtained from US Geological Survey (USGS) and
	USFS data.  Data is in raw form (not scaled) and contains
	binary (0 or 1) columns of data for qualitative independent
	variables (wilderness areas and soil types).
>
>	This study area includes four wilderness areas located in the
	Roosevelt National Forest of northern Colorado.  These areas
	represent forests with minimal human-caused disturbances,
	so that existing forest cover types are more a result of 
	ecological processes rather than forest management practices.
>
>	Some background information for these four wilderness areas:  
	Neota (area 2) probably has the highest mean elevational value of 
	the 4 wilderness areas. Rawah (area 1) and Comanche Peak (area 3) 
	would have a lower mean elevational value, while Cache la Poudre 
	(area 4) would have the lowest mean elevational value. 
>
>	As for primary major tree species in these areas, Neota would have 
	spruce/fir (type 1), while Rawah and Comanche Peak would probably
	have lodgepole pine (type 2) as their primary species, followed by 
	spruce/fir and aspen (type 5). Cache la Poudre would tend to have 
	Ponderosa pine (type 3), Douglas-fir (type 6), and 
	cottonwood/willow (type 4).  
>
>	The Rawah and Comanche Peak areas would tend to be more typical of 
	the overall dataset than either the Neota or Cache la Poudre, due 
	to their assortment of tree species and range of predictive 
	variable values (elevation, etc.)  Cache la Poudre would probably 
	be more unique than the others, due to its relatively low 
	elevation range and species composition. 

The data set contains the following features.

| Name                               |  Data Type    | Measurement                    |    Description                                 |
|------------------------------------|---------------|--------------------------------|------------------------------------------------|
| Elevation                          | quantitative  |    meters                      |  Elevation in meters                           |
| Aspect                             | quantitative  |    azimuth                     |  Aspect in degrees azimuth                     |
| Slope                              | quantitative  |    degrees                     |  Slope in degrees                              |
| Horizontal_Distance_To_Hydrology   | quantitative  |    meters                      |  Horz Dist to nearest surface water features   |
| Vertical_Distance_To_Hydrology     | quantitative  |    meters                      |  Vert Dist to nearest surface water features   |
| Horizontal_Distance_To_Roadways    | quantitative  |    meters                      |  Horz Dist to nearest roadway                  |
| Hillshade_9am                      | quantitative  |    0 to 255 index              |  Hillshade index at 9am, summer solstice       |
| Hillshade_Noon                     | quantitative  |    0 to 255 index              |  Hillshade index at noon, summer soltice       |
| Hillshade_3pm                      | quantitative  |    0 to 255 index              |  Hillshade index at 3pm, summer solstice       |
| Horizontal_Distance_To_Fire_Points | quantitative  |    meters                      |  Horz Dist to nearest wildfire ignition points |
| Wilderness_Area (4 binary columns) | qualitative   |    0 (absence) or 1 (presence) |  Wilderness area designation                   |
| Soil_Type (40 binary columns)      | qualitative   |    0 (absence) or 1 (presence) |  Soil Type designation                         |
| Cover_Type (7 types)               | integer       |    1 to 7                      |  Forest Cover Type designation                 |