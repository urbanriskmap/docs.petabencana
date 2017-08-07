## Alerts
Geospatial Alerting of Crowd-sourced Hazard Reports

{% method %}
### GET /alerts

Get all alert locations by user, including both subscribed and unsubscribed.

##### Required Parameters
- username (e.g. 'joe')
- network (e.g. 'twitter')

##### Optional Parameters
- format ('topojson' or 'geojson')

Example request

```sh
curl -X GET 'http://localhost:8001/alerts?username=joe&network=twitter&geoformat=geojson'
```

Example response

```javascript
{
    "statusCode": 200,
    "result": {
        "type": "FeatureCollection",
        "features": [
            {
                "type": "Feature",
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        12,
                        45
                    ]
                },
                "properties": {
                    "location_key": "19",
                    "userkey": "1",
                    "subscribed": null,
                    "username": "joe",
                    "network": "twitter",
                    "language": "en",
                    "alert_log": {
                        "test": 1
                    }
                }
            },
            {
                "type": "Feature",
                "geometry": {
                    "type": "Point",
                    "coordinates": [
                        12,
                        46
                    ]
                },
                "properties": {
                    "location_key": "20",
                    "userkey": "1",
                    "subscribed": null,
                    "username": "joe",
                    "network": "twitter",
                    "language": "en",
                    "alert_log": {
                        "test": 1
                    }
                }
            }
        ]
    }
}
```

### PUT /alerts
Update a user's alert location subscription and log. User and location are defined by userkey and location_key which are returned by the above GET /alerts endpoint. No parameters are required.

Example request

```sh
curl -X PUT \
  http://localhost:8001/alerts \
  -H 'content-type: application/json' \
  -d '{
    "userkey": "1",
    "location_key": "20",
    "subscribed":"false",
    "log_event":{"event":"unsubscribed"}
}'
```

Example response

```javascript
{
    "updated": true,
    "userkey": "1",
    "location_key": "19",
    "subscribed": false
}
```
