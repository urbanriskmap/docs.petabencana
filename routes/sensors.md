## Sensors

TODO

### Request Format

| URL Parameter | Description |
| -- | -- |


| Query Parameter | Description | Required? |
| -- | -- | -- |
| region | Which city do we wish to return infrastructure for? (one of `bdg`, `jbd`, `sby`) | Yes |
| format | What format should geographic results use (one of `topojson`, `geojson` defaults to `topojson`) | No |


{% method %}
### Sample Requests

{% sample lang="https" %}

Here is a simple HTTPS infrastructure request for sensors.

```https
curl "https://data.petabencana.id/v3/sensors/..."
```

{% common %}
Results are as follows:

```json
{
}
```

{% endmethod %}



