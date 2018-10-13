---
layout: post
title: creating bokeh plots in Jupyter
---

Developing interactive visualizations within your Jupyter notebook with Bokeh. Sometimes you would like to use jupyter for presenting your data science results. I required this when presenting my Python Machine learning project for the NYC Data Science Academy. It was useful to have interactive plots and have the ability to hover over certain points in the plot while presenting. I also wanted to use th pandas data frame and found you could intergrate pandas with the Bokeh library.


```
from bokeh.plotting import figure, show,output_notebook
from bokeh.resources import INLINE
#from bokeh.io import output_notebook
import numpy as np
import bokeh.io
# for using pandas with bokeh
import pandas as pd
from bokeh.models import ColumnDataSource
# for hovering
from bokeh.io import curdoc
from bokeh.models import HoverTool
```

To render your plot  within your jupyter notebook and convert the pandas data frame to bokeh.
```
bokeh.io.output_notebook(INLINE)
# convert pandas df to bokeh
source = ColumnDataSource(data = {'x' : data['col1'], 'y' : data['col2']})
```
Set your colours. 
```
#colormap = {'Y': 'red', 'N': 'green'}
#colors = [colormap[x] for x in data.Col1]
```

Then create a new plot with a title and axis labels.
```
p = figure(title = 'Relationship between Col1 and Col2',
                  x_axis_label = 'col1', y_axis_label = 'col2')
p.circle(x='x',y='y', source=source,radius=0.05)
```
Set the hover functionality.
````
hover = HoverTool(tooltips = [('col1', '@y'), ('col2|', '@x')])
p.add_tools(hover)
curdoc().add_root(p)
# show plot
show(p)

```

![_config.yml]({{ site.baseurl }}/images/bokeh.png)
