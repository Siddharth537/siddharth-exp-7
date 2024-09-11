# siddharth-exp-7
from bokeh.io import show
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.plotting import figure
from bokeh.layouts import column
import pandas as pd
import folium
# Load your data
data = pd.read_csv(r'C:\Users\sidda\Downloads\states.csv')
# Create a Bokeh figure
p = figure(width=800, height=400, tools='pan,wheel_zoom,reset')
# Create a ColumnDataSource to hold data
source = ColumnDataSource(data)
# Add circle markers to the figure
p.circle(x='longitude', y='latitude', size=10, source=source, color='orange')
# Create a hover tool for mouse rollover effect
hover = HoverTool()
hover.tooltips = [("Info", "@state_name"), ("Latitude", "@latitude"), ("Longitude", "@longitude")]
p.add_tools(hover)
# Display the Bokeh plot
layout = column(p)
show(layout)
# Create a map centered at a specific location
m = folium.Map(location=[Longitude,Latitude], zoom_start=10)
# Add markers for your data points
for index, row in data.iterrows():
    folium.Marker(
        location=[row['latitude'], row['longitude']],
        popup=row['Info'],  # Display additional info on mouse click
    ).add_to(m)
# Save the map to an HTML file
m.save('map.html')
![Screenshot (88)](https://github.com/user-attachments/assets/62cb5d63-f0a0-47e5-a90e-ccfae23f5d9d)
![Screenshot (89)](https://github.com/user-attachments/assets/1368771d-95ee-4534-b77f-5a58a89039de)
