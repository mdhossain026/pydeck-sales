
![download](https://github.com/mdhossain026/pydeck-sales/assets/531875/560dfdd3-1611-48fa-a619-200ab2040118)

# insatll pydeck via pip
pip install pydeck

# insatll pydeck via conda
conda install -c conda-forge pydeck

# create MAPBOX_API_KEY or GOOGLE_MAPS_API_KEY and set it 
set a MAPBOX_API_KEY or GOOGLE_MAPS_API_KEY environment variables, pydeck will detect them.


# import package

import pandas as pd
import pydeck
import pydeck as pdk

# read data from excel file
df = pd.read_excel('STL_ORDER_DATA.xlsx') ## reading .xlsx file to Pandas DataFrame

# layer creation
layer = pydeck.Layer(
    'HexagonLayer',
    df,
    get_position=['RETAILER_LONG', 'RETAILER_LAT'],
    auto_highlight=True,
    elevation_scale=50,
    pickable=True,
    elevation_range=[0,2000],
    extruded=True,
    coverage=1)

    # Set the viewport location
view_state = pdk.ViewState(
    longitude=90.263536,
    latitude=23.960293,
    zoom=8,
    min_zoom=5,
    max_zoom=15,
    pitch=10.5,
    bearing=-27.36)
# Combined all of it and render a viewport
r = pdk.Deck(layers=[layer], initial_view_state=view_state)
r.to_html('sales_data_location.html')



