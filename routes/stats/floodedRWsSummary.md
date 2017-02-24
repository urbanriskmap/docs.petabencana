## Stats (flooded RWs summary)

Count of all RWs by flood height range.

{% method %}
### GET /stats/floodedRWsSummary

{% sample lang="https" %}

```https
curl "https://data.petabencana.id/stats/floodedRWsSummary"
```

{% common %}
Results are as follows:

```json
{
  "# hati-hati RWs": 0,
  "# 10-70cm RWs": 9,
  "# 71-150cm RWs": 0,
  "# 151cm+ RWs": 0
}
```

{% endmethod %}
