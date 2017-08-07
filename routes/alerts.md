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

{% sample lang="https" %}


Example request

```https
curl -X GET 'http://localhost:8001/alerts?username=joe&network=twitter&geoformat=geojson'
```

{% common %}
The user was found:

```json
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

{% endmethod %}

{% method %}

### PUT /alerts
Update a user's alert location subscription and log. User and location are defined by userkey and location_key which are returned by the above GET /alerts endpoint. No parameters are required.

{% sample lang="https" %}

Example request to unsubscribe a user from an alert location.

```https
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

{% common %}
User location was updated successfully
```json
{
    "updated": true,
    "userkey": "1",
    "location_key": "19",
    "subscribed": false
}
```
{% endmethod %}


{% method %}
### POST  /alerts
Register a user location for alerts. If the user exists already, existing userkey will be assigned to the new location.

{% sample lang="https" %}

Example POST
```https
curl -X POST \
  http://localhost:8001/alerts \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -H 'postman-token: 2921a5db-0abc-6ca7-5878-c07d2d2c3ae8' \
  -d '{
	"username":"joe",
	"network":"twitter",
	"language":"en",
	"subscribed":"true",
	"location":{
		"lat": 1,
		"lng": 1
	}
}'
```

{% common %}
User created successfully
```json
{
    "created": true,
    "userkey": "6",
    "location_key": "32"
}
```

{% endmethod %}
