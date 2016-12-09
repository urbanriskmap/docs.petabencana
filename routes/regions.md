## Regions

Petanbencana supports multiple regions defined by a geographic area.  This endpoint will return the supported regions together with their geographic bounds.


### Request Format

| Query Parameter | Description | Format | Required |
| -- | -- | -- | -- |
| city | Which city do we wish to return infrastructure for? (one of `bdg`, `jbd`, `sby`) | String | No |
| format | Which format should we return results in? (one of `json`, defaults to `json`) | String | No |
| geoformat | What format should geographic results use (one of `topojson`, `geojson` defaults to `topojson`) | String | No |


{% method %}
### GET /regions

{% sample lang="https" %}

Return all regions in default (topojson) format.

```https
curl "https://data.petabencana.id/regions"
```

{% common %}
Results are as follows:

```json
{
  "statusCode": 200,
  "result": {
    "type": "Topology",
    "objects": {
      "output": {
        "type": "GeometryCollection",
        "geometries": [
          {
            "type": "Polygon",
            "properties": {
              "code": "jbd",
              "name": "Jabodetabek"
            },
            "arcs": [
              [
                0
              ]
            ]
          },
          {
            "type": "Polygon",
            "properties": {
              "code": "bdg",
              "name": "Bandung"
            },
            "arcs": [
              [
                1
              ]
            ]
          },
          {
            "type": "Polygon",
            "properties": {
              "code": "sby",
              "name": "Surabaya"
            },
            "arcs": [
              [
                2
              ]
            ]
          }
        ]
      }
    },
    "arcs": [
      [
        [
          0,
          4891
        ],
        [
          1061,
          0
        ],
        [
          0,
          5108
        ],
        [
          -1061,
          0
        ],
        [
          0,
          -5108
        ]
      ],
      [
        [
          1357,
          2305
        ],
        [
          857,
          0
        ],
        [
          0,
          2976
        ],
        [
          -857,
          0
        ],
        [
          0,
          -2976
        ]
      ],
      [
        [
          9031,
          0
        ],
        [
          968,
          0
        ],
        [
          0,
          3207
        ],
        [
          -968,
          0
        ],
        [
          0,
          -3207
        ]
      ]
    ],
    "transform": {
      "scale": [
        0.0006552455245524552,
        0.000167006700670067
      ],
      "translate": [
        106.48,
        -7.5499
      ]
    },
    "bbox": [
      106.48,
      -7.5499,
      113.0318,
      -5.88
    ]
  }
}
```

Return all regions in default (geojson) format.

```https
curl "https://data.petabencana.id/regions?geoformat=geojson"
```

{% common %}
Results are as follows:

```json
{
  "statusCode": 200,
  "result": {
    "type": "FeatureCollection",
    "features": [
      {
        "type": "Feature",
        "geometry": {
          "type": "Polygon",
          "coordinates": [
            [
              [
                106.48,
                -6.733
              ],
              [
                107.175,
                -6.733
              ],
              [
                107.175,
                -5.88
              ],
              [
                106.48,
                -5.88
              ],
              [
                106.48,
                -6.733
              ]
            ]
          ]
        },
        "properties": {
          "code": "jbd",
          "name": "Jabodetabek"
        }
      },
      {
        "type": "Feature",
        "geometry": {
          "type": "Polygon",
          "coordinates": [
            [
              [
                107.369,
                -7.165
              ],
              [
                107.931,
                -7.165
              ],
              [
                107.931,
                -6.668
              ],
              [
                107.369,
                -6.668
              ],
              [
                107.369,
                -7.165
              ]
            ]
          ]
        },
        "properties": {
          "code": "bdg",
          "name": "Bandung"
        }
      },
      {
        "type": "Feature",
        "geometry": {
          "type": "Polygon",
          "coordinates": [
            [
              [
                112.3975,
                -7.5499
              ],
              [
                113.0318,
                -7.5499
              ],
              [
                113.0318,
                -7.0143
              ],
              [
                112.3975,
                -7.0143
              ],
              [
                112.3975,
                -7.5499
              ]
            ]
          ]
        },
        "properties": {
          "code": "sby",
          "name": "Surabaya"
        }
      }
    ]
  }
}
```


{% endmethod %}



