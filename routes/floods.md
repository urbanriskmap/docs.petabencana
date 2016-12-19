## Floods

Live flood information - by city, by flood state (if required).  Supports a /states endpoint which is non-geographic and simply gives the state of flooded areas as well as a geographic endpoint which will give flooded areas subject to a minimum_state or all areas together with their current flood status.  In addition to [topojson](https://github.com/topojson/topojson/wiki) and [geojson](http://geojson.org/) this endpoint supports the [Common Alerting Protocol (CAP)](https://en.wikipedia.org/wiki/Common_Alerting_Protocol)


### Flood State Codes

Numeric codes are used to represent flood states, these are as follows:

| Code | Severity | Description |
| -- | -- | -- |
| 1 | Unknown | AN UNKNOWN LEVEL OF FLOODING - USE CAUTION - |
| 2 | Minor | FLOODING OF BETWEEN 10 and 70 CENTIMETERS |
| 3 | Moderate | FLOODING OF BETWEEN 71 and 150 CENTIMETERS |
| 4 | Severe | FLOODING OF OVER 150 CENTIMETERS |


### Request Format

| Query Parameter | Description | Format | Required |
| -- | -- | -- | -- |
| city | Which city do we wish to return infrastructure for? (one of `bdg`, `jbd`, `sby`) | String | No |
| format | Which format should we return results in? (one of `json`, `xml`, defaults to `json`) | String | No |
| geoformat | What format should geographic results use (one of `topojson`, `geojson`, `cap` defaults to `topojson`) | String | No |
| minimum_state | The minimum flood state that should be returned? (one of `1`, `2`, `3`, `4`) | Number | No |



{% method %}
### GET /floods

{% sample lang="https" %}

List all current floods in Jakarta.

```https
curl "https://data.petabencana.id/floods?city=jbd"
```

{% common %}
Results are as follows:

```json
{
  // Details to follow
}
```

{% sample lang="https" %}

List all current floods in Jakarta in CAP format.

```https
curl "https://data.petabencana.id/floods?city=jbd&format=xml&geoformat=cap"
```

{% common %}
Results are as follows:

```xml
<?xml version="1.0"?>
<feed xmlns="http://www.w3.org/2005/Atom">
    <id>https://data.petabencana.id/floods</id>
    <title>petabencana.id Flood Affected Areas</title>
    <updated>2016-12-09T21:29:45+07:00</updated>
    <author>
        <name>petabencana.id</name>
        <uri>https://petabencana.id/</uri>
    </author>
    <!-- Details to follow -->
</feed>
```


{% endmethod %}



