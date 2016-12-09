## Feeds

Petabencana utilises data feeds from a number of third party sources.  This endpoint allows the creation of data into the system for authorised users.  Note: [authentication](https://docs.petabencana.id/general/authentication.html) is required to post data through the /feeds endpoint.

{% method %}
### POST /feeds/qlue

Add a report to the system from Qlue.  The following attributes are supported for Qlue reports:

| Attribute | Description | Format | Required |
| -- | -- | -- | -- |
| post_id | Unique qlue identifier for the report | Integer | Yes |
| created_at | Date and time the card was created | Date ([ISO 8601](http://www.iso.org/iso/home/standards/iso8601.htm)) | Yes |
| title | The title of the report being filed | String | No |
| text | Description of the disaster event | String | No |
| image_url | URL of the associated image | String | No |
| qlue_city | From which city was the report generated (must be one of `jabodetabek`, `bandung`, `surabaya`) | String | Yes |
| disaster_type | What type of disaster is being reported (currently only `flood`is supported) | String | Yes |
| location | Geographic location of the disaster event | Lat/Lng in [ESPG:4326](http://spatialreference.org/ref/epsg/wgs-84/) | Yes |


{% sample lang="https" %}

Here is a simple call to POST a new Qlue report:

```https
curl -X POST -H "X-Api-Key: API_KEY_GOES_HERE" -d '{
    "post_id":1234567802,
    "created_at":"2016-12-09T11:32:52.011Z",
    "image_url":"http://myimg",
    "qlue_city":"jabodetabek",
    "disaster_type":"flood",
    "text":"A big flood",
    "location": {
        "lat": -6.149531,
        "lng": 106.869342
    }
}' "https://data.petabencana.id/feeds/qlue"
```

{% common %}
Report was successfully created:

```json
{
  "post_id": 1234567802,
  "created": true
}
```

{% common %}
The request was successful however the report already exists:

```json
{
  "post_id": 1234567802,
  "created": false,
  "message": "1234567802 already exists in reports table"
}
```

{% endmethod %}



