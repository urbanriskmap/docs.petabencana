## Stats (flooded regions summary)

List of all regions with currently flooded RWs.

### Request Format

| Query Parameter | Description | Format | Required |
| -- | -- | -- | -- |
| city | Which city do we wish to return infrastructure for? (one of `bdg`, `jbd`, `sby`) | String | No |

{% method %}
### GET /stats/floodedRegionsSummary

{% sample lang="https" %}

```https
curl "https://data.petabencana.id/stats/floodedRegionsSummary?city=jbd"
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
