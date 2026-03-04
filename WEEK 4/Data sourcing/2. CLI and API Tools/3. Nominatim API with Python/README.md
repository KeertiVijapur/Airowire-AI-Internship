# Nominatim API with Python (Geocoding) - (https://www.youtube.com/watch?v=f0PZ-pphAXE)

## What I Learned

In this session, I learned how to convert a place name or address into **latitude and longitude coordinates** using the **Nominatim Geocoding API** through the `geopy` Python library.

Nominatim is based on **OpenStreetMap** and works similarly to Google Maps for geocoding, but it is open-source.

---

## Tools Used

```python
geopy
Nominatim (from geopy.geocoders)
```

---

## Basic Workflow

1. Import Nominatim
2. Create a geocoder object with a user agent
3. Call `.geocode("place name")`
4. Extract required fields

Example:

```python
from geopy.geocoders import Nominatim

geolocator = Nominatim(user_agent="my_app")
location = geolocator.geocode("IIT Madras")

print(location.latitude, location.longitude)
```

---

## Data Extracted

From a single query, we can get:

* Latitude
* Longitude
* Full formatted address
* Bounding box
* Place class (e.g., tourism, amenity)
* Place type (e.g., university, attraction)

---

## Example Results

| Query        | Type                 | Notes                               |
| ------------ | -------------------- | ----------------------------------- |
| Eiffel Tower | Tourism / Attraction | Returned full address + coordinates |
| IIT Madras   | Amenity / University | Included postal code 600036         |

---

## Important Notes

* Must specify a **user_agent** while creating Nominatim object.
* If you get HTTP 403 error, use your email or name in user_agent.
* Works in both local Python and Google Colab.
## Key Takeaways

* Geocoding converts text → geographic coordinates.
* OpenStreetMap provides rich open-source geodata.
* `geopy` simplifies API interaction.
* Useful for mapping, location analytics, and spatial data processing.
