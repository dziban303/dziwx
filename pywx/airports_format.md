# Airports Database Information

Airports.dat is a CSV file containing the list of world airports used by the dziwx bot for location and weather lookups. The file is based on the OpenFlights database file of the same name, from the [OpenFlights GitHub repository](https://github.com/jpatokal/openflights/tree/master/data). The point of divergence is unknown, but it was at least five years ago, and the two files have numerous differences now. Besides the many changes to the remote file, I've added some airports manually, and removed a few that don't exist. I dropped some fields of the original file. Reconciling and merging for completeness' sake would be nice, but it **is not** gonna be worth the time. 

# CSV Fields

The CSV is in the following format:
`id,name,city,country,iata,icao,lat,lon,alt,tz_offset,dst_type`

* `id` = a numeric identifier. It was sequential once but now it's ~1500 off.
* `name` = The airport's common name.
* `city` = The city, town, or other place in which the airport is located.
* `iata` = Three-character IATA code for the airport.
* `icao` = Four-character ICAO code for the airport.
* `lat` = Latitude.
* `lon` = Longitude.
* `alt` = Altitude above sea level of the airport.
* `tz_offset` = Shows the difference from UTC in hours. -6 would be Central Standard Time (CST), +4 would be Moscow Standard Time (MSK), et cetera.
* `dst_type` = Shows the *approximate* schedule for Daylight Saving Time at the airport's location. The codes are as follows:
  * E (Europe), 
  * A (US/Canada), 
  * S (South America), 
  * O (Australia), 
  * Z (New Zealand), 
  * N (None), or 
  * U (Unknown).

Since the DST start and end dates may fluctuate from year to year, this method provides a general idea of when DST will be in effect. Generally speaking, DST implementations occur on the same day in a given state, region, nation, even continent. But there are plenty of exceptions, so the accuracy of even this broad-stroke approach is questionable. And, of course, these codes are as dated as the rest of the file and the DST schedule may have wildly changed.