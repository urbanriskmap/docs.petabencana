## Infrastructure

Locations of local infrastructure including flood gates, pumps and waterways

### Request Format

| URL Parameter | Description |
| -- | -- |
| infrastructure_type | What type of infrastructure do we wish to list?  (one of `floodgates`, `pumps`, `waterways`) |


| Query Parameter | Description | Required? |
| -- | -- | -- |
| region | Which city do we wish to return infrastructure for? (one of `bdg`, `jbd`, `sby`) | Yes |
| format | What format should geographic results use (one of `topojson`, `geojson` defaults to `topojson`) | No |


{% method %}
### Sample Requests

{% sample lang="https" %}

Here is a simple HTTPS infrastructure request for pumps.

```https
curl "https://data.petabencana.id/v3/infrastructure/pumps?city=jbo"
```

{% common %}
Results are as follows:

```json
{
  "type": "Topology",
  "objects": {
    "output": {
      "type": "GeometryCollection",
      "geometries": [
        {
          "type": "Point",
          "properties": {
            "name": "PA Marina"
          },
          "coordinates": [
            7164,
            7352,
            0
          ]
        },
        {
          "type": "Point",
          "properties": {
            "name": "Pompa Waduk Setia Budi Barat"
          },
          "coordinates": [
            5312,
            5077,
            0
          ]
        },

        // results continue....

        {
          "type": "Point",
          "properties": {
            "name": "Pompa UP Senen"
          },
          "coordinates": [
            6143,
            6544,
            0
          ]
        }
      ]
    }
  },
  "arcs": [],
  "transform": {
    "scale": [
      0.000020651319451945148,
      0.000020217245084508508
    ],
    "translate": [
      106.7188310623,
      -6.3060956581
    ]
  },
  "bbox": [
    106.7188310623,
    -6.3060956581,
    106.9253236055,
    -6.1039434245
  ]
}
```

{% endmethod %}



