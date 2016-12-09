## Floods

Live flood reports, by default reports will be returned for the last hour.  In addition to [topojson](https://github.com/topojson/topojson/wiki) and [geojson](http://geojson.org/) this endpoint supports the [Common Alerting Protocol (CAP)](https://en.wikipedia.org/wiki/Common_Alerting_Protocol)


### Request Format

| Query Parameter | Description | Format | Required |
| -- | -- | -- | -- |
| city | Which city do we wish to return infrastructure for? (one of `bdg`, `jbd`, `sby`) | String | No |
| format | Which format should we return results in? (one of `json`, `xml`, defaults to `json`) | String | No |
| geoformat | What format should geographic results use (one of `topojson`, `geojson`, `cap` defaults to `topojson`) | String | No |


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



