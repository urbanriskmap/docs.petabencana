## Stats (flooded regions summary)

List of all regions with currently flooded RWs.

{% method %}
### GET /stats/floodedRegionsSummary

{% sample lang="https" %}

```https
curl "https://data.petabencana.id/stats/floodedRegionsSummary"
```

{% common %}
Results are as follows:

```json
{
  "total number of regions with flooded RWs": 4,
  "regions with flooded RWs": [
    "KAPUK",
    "RAWA TERATE",
    "CIPINANG MELAYU",
    "CENGKARENG BARAT"
  ]
}
```

{% endmethod %}
