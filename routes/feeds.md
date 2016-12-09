## Feeds

Petabencana utilises data feeds from a number of third party sources.  This endpoint allows the creation of data into the system for authorised users.  Note: [authentication](https://docs.petabencana.id/general/authentication.html) is required to post data through the /feeds endpoint.

{% method %}
### POST /feeds/qlue

Add a report to the system from Qlue:

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



