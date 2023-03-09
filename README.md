# Cotton Phenology Dataset :seedling:

The dataset contains labels about the phenological stages of cotton at the parcel level, generated by in-situ inspections in the region of Orchomenos, Greece, during the cotton cultivation period of 2021 (May-October). We collected 1,285 crop growth ground observations. We introduce a new collection protocol, assigning up to two phenology labels that represent the primary and secondary growth stage in the field and thus indicate when stages are transitioning. More information about the annotation procedure can be found in the relevant publication ["Fuzzy clustering for the within-season estimation of cotton phenology"](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0282364#). Specifically the dataset is composed of:
- a csv file which includes: 
  - the main and secondary (if exist) phenological stage and its percentage for each in-situ visit in parcel level.
  - the metalabel for each in-situ visit (as they are described in the paper).
  - the date of the in-situ visit
  - the nearest sentinel-2 acquistion date for each in-situ visit.
  - the sowing and the haverst (if available) dates for each parcel

- a geojson file containing the geometries of all the parcels.

- the nearest sentinel-2 acquistion Each image is named in the following format:
`{date}_{id}-{type}.jpg`, where `date` is in the format `{year}{month}{day}` and refes to the exact date that the image was captured, `id` is the unique id of a parcel and `type` is one of `O`, `A` or `B`. `O` refers to a panoramic photo of the entire field, `A` to a photo that is representative of the majority of the plants in the field and `B` to one representative of a minority of plants in the field. For each date and each unique parcel the first two exists always while the latter close-up photo had be captured only when the percentage of the minority class, in terms of area, was deemed significant. 

### Reference

If you use this dataset please cite the publication below
```
@article{10.1371/journal.pone.0282364,
    doi = {10.1371/journal.pone.0282364},
    author = {Sitokonstantinou, Vasileios AND Koukos, Alkiviadis AND Tsoumas, Ilias AND Bartsotas, Nikolaos S. AND Kontoes, Charalampos AND Karathanassi, Vassilia},
    journal = {PLOS ONE},
    title = {Fuzzy clustering for the within-season estimation of cotton phenology},
    year = {2023},
    url = {https://doi.org/10.1371/journal.pone.0282364},
    volume = {18},
    number = {3},
}
```

## Downloading the phenology dataset through direct links
To download the data, you can use the following links, taken from [the corresponding page of the dataset on Zenodo](https://zenodo.org/record/7646864):
* Phenology ground observations [(download link)](https://zenodo.org/record/7646864/files/in_situ_cotton_phenology_labels.csv?download=1)
* Parcels' geometries [(download link)](https://zenodo.org/record/7646864/files/parcels.geojson?download=1)
* Field images [(download link)](https://zenodo.org/record/7646864/files/cotton_phenology_in-situ_photos_2021.zip?download=1)
  * _file size: ~12.3GB
<br/><br/>


## Downloading phenology dataset through the provided download script
An alternative way to download the dataset, is to use the `download.sh` script included in this repository. The instructions for the script usage are as follows:

1. download the .csv with the ground observations and the corresponing geojson file of the parcels' geometries to `data/`
```bash
bash download.sh phenology
```
2. download field images to `data/images` (~ 12.3GB)
  ```bash
  bash download.sh images
  ````
or download everything with `bash download.sh all`
<br/><br/>

## Overview

### 1286 Unique Visits in 80 Parcels 

<p float="center">
<img src="https://github.com/Agri-Hub/cotton-phenology-dataset/blob/main/images/parcels.png" width="480" height="480">
<img src="https://github.com/Agri-Hub/cotton-phenology-dataset/blob/main/images/labeled_parcels_all.png" width="480" height="480">
</p>

### Overall Statistics

| Phenological stage | # Main | # Secondary | Code[^1] |
| --- | --- | --- | --- |
| `Root Establishment` | 75 | 4 | 1 |
| `Leaf Development` | 422 | 20 | 2 |
| `Squaring` | 212 | 6 | 3 |
| `Flowering` | 229 | 149 | 4 |
| `Boll Development` | 251 | 313 | 5 |
| `Boll Opening` | 97 | 177 | 6 |
| **`Total`**[^2]  | **1286** | **668** | - |

The  field  visits  were  appropriately  scheduled  in  order  to have  minimal  differences  between  ground  and  satellite  observations.  Thus, difference between  the  ground  and  the Sentinel-2 observation was `mean = 0.86 days` with `standard deviation = 0.89 days` .

#### Empirical cumulative distribution functions
of main & secondary stages as recorded by inspector
<img src="https://github.com/Agri-Hub/cotton-phenology-dataset/blob/main/images/ecdf_plot_12.png?raw=true" alt="ecdf_plot_12" width="700"/>

### Photos

<table>
  <tr>
    <td>Main stage</td>
     <td>Secondary stage</td>
     <td>Panoramic</td>
  </tr>
  <tr>
    <td><img src="(https://github.com/Agri-Hub/cotton-phenology-dataset/blob/main/insitu-photos/demo_sample/20210616_0001-A.jpg?raw=true" width=270 height=480></td>
    <td><img src="(https://github.com/Agri-Hub/cotton-phenology-dataset/blob/main/insitu-photos/demo_sample/20210616_0001-B.jpg?raw=true" width=270 height=480></td>
    <td><img src="(https://github.com/Agri-Hub/cotton-phenology-dataset/blob/main/insitu-photos/demo_sample/20210616_0001-O.jpg?raw=true" width=270 height=480></td>
  </tr>
 </table>

### Acknowledgements
The polygons of parcels stem from [Agriculture Cooperative of Orchomenos](https://asoo.gr/)

This work is part of e-shape's[^3] pilot [S1P2 EU CAP Support](https://e-shape.eu/index.php/showcases/pilot1-2-eu-cap-support) by the [Beyond Center of Excellence](http://beyond-eocenter.eu/) of the National Observatory of Athens.

Researchers:  Alkiviadis Marios Koukos (akoukos@noa.gr), Vasileios Sitokonstantinou (vsito@noa.gr), Ilias Tsoumas (i.tsoumas@noa.gr)

[^1]: A `code=0` placed inside the cells of `.csv` in the cases of absence of secondary phenological stage.
[^2]: Given that some in-situ visits differed the same number of days from two Sentinel-2 acquisitions we have in total 1524 Sentinel-2 acquisitions in which are assigned in-situ visit.
[^3]: The e-shape project has received funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement 820852



