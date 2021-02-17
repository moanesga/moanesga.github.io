## EDA for Pneumonia detection from chest X-Rays (NIH)

**Project description:** Exploratory data analysis (EDA) of NIH dataset that contains 2D medical imaging data (X-Ray). Exploration of python libraries to extract 2D images from DICOM files and further statistical analysis like demographic data, distribution of related diseases, illness presence per patient and histograms of intensity values as pixel-level assesments of the imaging data to differenciate healthy and illness states. 

Source: AI for Healthcare Udacity Nanodegree program 


### 1. Importing python libraries 

```python
import numpy as np # linear algebra
import pandas as pd # data processing, CSV file I/O (e.g. pd.read_csv)
import os
from glob import glob
%matplotlib inline
import matplotlib.pyplot as plt
import seaborn as sns
from skimage.io import imread, imshow
import pydicom
from random import sample
from itertools import chain 
import scipy
import skimage
```

### 2. Reading the xray date into a pandas DataFrame

```python
all_xray_df = pd.read_csv('/data/Data_Entry_2017.csv')
all_xray_df.sample(3)
```

<img src="images/EDA_01.PNG?raw=true"/>


### 3. Using matplotlib.pyplot to create a Bar Chart of X-rays labeled Images 

Finding Labels: All labels(15):['Atelectasis', 'Cardiomegaly', 
'Consolidation', 'Edema', 'Effusion', 'Emphysema', 'Fibrosis',
'Hernia', 'Infiltration', 'Mass', 'No Finding', 'Nodule', 'Pleural_Thickening',
'Pneumonia', 'Pneumothorax'] 


```python
ax = all_xray_df[all_labels].sum().plot(kind = 'bar')
ax.set(ylabel = 'Number of images with label')
```

<img src="images/EDA_02.PNG?raw=true"/>


### 4. Extracting number of X-Ray images labeled with presence of Pneumonia

Out of the 112.120 X-ray images, 1431 are labeled with presence of Pneumonia, 
which accounts for approximately 1,28% of the whole dataset.

```python
len(all_xray_df[all_xray_df.Pneumonia == 1])
```


### 5. Loading sample data for pixel level assessments


```python
sample_df = pd.read_csv('sample_labels.csv')
sample_df.sample(3)
```

<img src="images/EDA_03.PNG?raw=true"/>


### 6. Showing sample with presence of Pneumonia and without Pneumonia


```python
img_ps = [glob(f"/data/images*/*/{i}")[0] for i in sample["Image Index"].values]

_, axs = plt.subplots(2,2, figsize =(10, 12))
axs = axs.flatten()

for img_p, ax in zip(img_ps, axs):
    
    img = plt.imread(img_p)
    ax.set_title(sample[sample['Image Index']==img_p.split('/')[-1]]['Finding Labels'].values[0])
    ax.axis('Off')
    ax.imshow(img, cmap ='gray')

plt.show()
```

<img src="images/EDA_04.PNG?raw=true"/>


### 7. Plotting histograms of intensity values comparing presence of Pneumonia and No Pneumonia

No Pneumonia (Blue) - Pneumonia (Red)

```python
plt.figure(figsize = (5,5))
plt.hist(chest_ray_no_pneumonia.ravel(), bins =256, color = 'blue')
plt.hist(chest_ray_pneumonia.ravel(), bins =256, color = 'red')
plt.show()
```

<img src="images/EDA_05.PNG?raw=true"/>



For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
