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
| minimum_state | The minimum flood state that should be returned? (min: `1`, max: `4`) | Number | No |



{% method %}
### GET /floods

{% sample lang="https" %}

List all flooded areas in Jakarta with a flood state of 1 or higher.

```https
curl "https://data.petabencana.id/floods?city=jbd&minimum_state=1"
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
              "area_id": "5",
              "geom_id": "3174040004009000",
              "area_name": "RW 09",
              "city_name": "Jakarta",
              "state": 1,
              "last_updated": "2016-12-19T13:53:52.274Z"
            },
            "arcs": [
              [
                0
              ]
            ]
          }
        ]
      }
    },
    "arcs": [
      [
        [
          9999,
          7847
        ],
        [
          -507,
          -6
        ],
        [
          -695,
          -70
        ],
        [
          -317,
          -221
        ],
        [
          -761,
          -18
        ],
        [
          -516,
          98
        ],
        [
          -641,
          -61
        ],
        [
          -649,
          -119
        ],
        [
          -169,
          -762
        ],
        [
          -181,
          -519
        ],
        [
          48,
          -602
        ],
        [
          -130,
          -162
        ],
        [
          64,
          -1235
        ],
        [
          81,
          -2351
        ],
        [
          136,
          -1098
        ],
        [
          15,
          -675
        ],
        [
          -1250,
          -40
        ],
        [
          -879,
          -6
        ],
        [
          -924,
          217
        ],
        [
          -924,
          425
        ],
        [
          -1800,
          138
        ],
        [
          830,
          1540
        ],
        [
          565,
          1455
        ],
        [
          764,
          1975
        ],
        [
          1018,
          2079
        ],
        [
          384,
          788
        ],
        [
          389,
          1061
        ],
        [
          1398,
          -76
        ],
        [
          296,
          -25
        ],
        [
          360,
          6
        ],
        [
          392,
          -9
        ],
        [
          360,
          -9
        ],
        [
          377,
          12
        ],
        [
          323,
          25
        ],
        [
          354,
          76
        ],
        [
          296,
          89
        ],
        [
          211,
          42
        ],
        [
          290,
          52
        ],
        [
          217,
          28
        ],
        [
          341,
          110
        ],
        [
          43,
          -67
        ],
        [
          57,
          -174
        ],
        [
          109,
          -159
        ],
        [
          154,
          -257
        ],
        [
          115,
          -370
        ],
        [
          99,
          -346
        ],
        [
          124,
          -357
        ],
        [
          133,
          -422
        ]
      ]
    ],
    "transform": {
      "scale": [
        0.0000003311331833192323,
        0.00000032713269326930546
      ],
      "translate": [
        106.7917869997,
        -6.158925
      ]
    },
    "bbox": [
      106.7917869997,
      -6.158925,
      106.7950980004,
      -6.1556540002
    ]
  }
}
```

{% sample lang="https" %}

List all flooded areas in Jakarta with a flood state of 1 or higher in CAP format.

```https
curl "https://data.petabencana.id/floods?city=jbd&minimum_state=1&format=xml&geoformat=cap"
```

{% common %}
Results are as follows:

```xml
<?xml version="1.0"?>
<feed xmlns="http://www.w3.org/2005/Atom">
    <id>https://data.petabencana.id/floods</id>
    <title>petabencana.id Flood Affected Areas</title>
    <updated>2016-12-19T22:01:48+07:00</updated>
    <author>
        <name>petabencana.id</name>
        <uri>https://petabencana.id/</uri>
    </author>
</feed>
```
{% endmethod %}



{% method %}
### GET /floods/states

{% sample lang="https" %}

List all flooded area states in Jakarta with a flood state of 1 or higher.

```https
curl "https://data.petabencana.id/floods/states?city=jbd&minimum_state=1"
```

{% common %}
Results are as follows:

```json
{
  "statusCode": 200,
  "result": [
    {
      "area_id": "5",
      "state": 1,
      "last_updated": "2016-12-19T13:53:52.274Z"
    }
  ]
}
```
{% endmethod %}


{% method %}
### PUT /floods/:localAreaId

{% sample lang="https" %}

PUT a new flood state in the system for a given local area (secure, requires authorisation token).

```https
curl "https://data.petabencana.id/floods/states?city=jbd&minimum_state=1"
```

{% common %}
Results are as follows:

```json
{
  "statusCode": 200,
  "result": [
    {
      "area_id": "5",
      "state": 1,
      "last_updated": "2016-12-19T13:53:52.274Z"
    }
  ]
}
```
{% endmethod %}










