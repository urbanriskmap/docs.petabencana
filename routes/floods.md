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
  "statusCode": 200,
  "result": {
    "type": "Topology",
    "objects": {
      "output": {
        "type": "GeometryCollection",
        "geometries": [
          {
            "type": "Point",
            "properties": {
              "pkey": "869",
              "fkey": "869",
              "database_time": "2016-12-08T11:23:40.892Z",
              "created_at": "2016-12-08T18:20:00.000Z",
              "text": "Jalan Marinir barat blok AC Pondok kelapa.. Kavling Marinir #drainaseburuk setinggi 30cm",
              "source": "qlue",
              "status": "confirmed",
              "disaster_type": "flood",
              "lang": null,
              "url": null,
              "image_url": "https://lh3.googleusercontent.com/DCivZPLE2o23V0cIqgGbvVMEz0mscHtmrUHR0uKuvZSdtWYPcB4P0Ej0lFQHP0HmtN33q2FyRg9OtHDfZXihbvu9GLo=s480-c",
              "title": " ",
              "report_data": null,
              "tags": {
                "instance_region_code": "jbd",
                "local_area_id": "1710"
              }
            },
            "coordinates": [
              9445,
              2690
            ]
          },
          {
            "type": "Point",
            "properties": {
              "pkey": "264",
              "fkey": "264",
              "database_time": "2016-12-08T00:53:40.883Z",
              "created_at": "2016-12-08T07:53:00.000Z",
              "text": "#drainaseburuk mampet. Tidak mengalir. Kapan dikeruk yg serius? Dari depan pasar sampai lampu merah.",
              "source": "qlue",
              "status": "confirmed",
              "disaster_type": "flood",
              "lang": null,
              "url": null,
              "image_url": "https://lh3.googleusercontent.com/pmJVamKBGuHhBf7N6F8clzXGeQUmSPKghG_LPgSSN7lLQeQwwtcoq8mmFbVebv8ZC1LVyXW_OG5XH_7Ad19J1eKMLtWNoQ=s480-c",
              "title": " ",
              "report_data": null,
              "tags": {
                "instance_region_code": "jbd",
                "local_area_id": "2514"
              }
            },
            "coordinates": [
              3191,
              9447
            ]
          },
          {
            "type": "Point",
            "properties": {
              "pkey": "11",
              "fkey": "11",
              "database_time": "2016-12-07T21:02:25.361Z",
              "created_at": "2016-12-08T03:50:00.000Z",
              "text": "Lumpur nya terlalu tinggi mohon agar di TL stiap hujan selalu banjir",
              "source": "qlue",
              "status": "confirmed",
              "disaster_type": "flood",
              "lang": null,
              "url": null,
              "image_url": "https://lh3.googleusercontent.com/c701LEHjl8VsNIaUx9UeIP86Oxfu7JCi8mm-pWj-V_GcmnKQBrbmT-DJi4ll4S-PZ0uVs1-3aSv67ovyVqql2YuVp7T1=s480-c",
              "title": " ",
              "report_data": null,
              "tags": {
                "instance_region_code": "jbd",
                "local_area_id": "202"
              }
            },
            "coordinates": [
              3,
              6219
            ]
          },
          // etc. etc. //
          {
            "type": "Point",
            "properties": {
              "pkey": "909",
              "fkey": "909",
              "database_time": "2016-12-08T11:43:40.388Z",
              "created_at": "2016-12-08T18:43:00.000Z",
              "text": "Banjir besar di kampung pengarengan Rt.010/06,\nHujan deras yg mengguyur  mengakibatkan banjir besar  karena saluran air yg sudah \nTidak bisa menampung debit .",
              "source": "qlue",
              "status": "confirmed",
              "disaster_type": "flood",
              "lang": null,
              "url": null,
              "image_url": "https://lh3.googleusercontent.com/bAqVqUuAA_p24ad6Aup2xnRq4XuwOs27Z-Iy3KSiJX7LRGs-AsLIWSDmZv6vCgGOi5Oy0-K633tftH0-Ig2fTwQP0oXG=s480-c",
              "title": "Banjir besar ",
              "report_data": null,
              "tags": {
                "instance_region_code": "jbd",
                "local_area_id": "1454"
              }
            },
            "coordinates": [
              9428,
              4914
            ]
          }
        ]
      }
    },
    "arcs": [],
    "transform": {
      "scale": [
        0.00002091809180918205,
        0.000014467646764676497
      ],
      "translate": [
        106.726311,
        -6.275664
      ]
    },
    "bbox": [
      106.726311,
      -6.275664,
      106.935471,
      -6.131002
    ]
  }
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
</feed>
```


{% endmethod %}



