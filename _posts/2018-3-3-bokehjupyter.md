---
layout: post
title: creating bokeh plots in Jupyter
---

Developing interactive visualizations within your Jupyter notebook with Bokeh.


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

# to render within nb
bokeh.io.output_notebook(INLINE)
# convert pandas df to bokeh
source = ColumnDataSource(data = {'x' : data['col1'], 'y' : data['col2']})

#colormap = {'Y': 'red', 'N': 'green'}
#colors = [colormap[x] for x in data.Loyalty_Program]


# create a new plot with a title and axis labels
p = figure(title = 'Relationship between Col1 and Col2',
                  x_axis_label = 'col1', y_axis_label = 'col2')
p.circle(x='x',y='y', source=source,radius=0.05)

#hover
hover = HoverTool(tooltips = [('col1', '@y'), ('col2|', '@x')])
p.add_tools(hover)
curdoc().add_root(p)
# show the results

show(p)
```
![_config.yml]({{ site.baseurl }}/images/bokeh.png)
