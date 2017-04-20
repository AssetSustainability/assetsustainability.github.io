---
title: Motors@Work API Overview
layout: helpfile
categories: ['api']
permalink: api-overview/
sequence: 1
tags:
- api
---
## Motors@Work APIs
Connect with the Motors@Work using the JSON-based RESTful API.  The Motors@Work REST/HTTP API allows you to send motor and motor based system readings to the Motors@Work analytics engine.

### Authentication
The Motors@Work public API uses REST which requires authentication on every request. The API expects HTTP basic access authentication to be included with each request and each request must be made over HTTPS.

### Endpoints

| Endpoint                                                      | HTTP verb     | Purpose                  |
| ------------------------------------------------------------- |:-------------:| ------------------------ |
| /api/1.0/rest/test                                            | GET           | [Authentication Testing](#Authentication Testing) |
| /api/1.0/rest/motor/external/measurement                      | PUT           | Adding a measurement     |

#### <a name="Authentication Testing"></a> Authentication Testing
Test your Motors@Work authentication by sending a GET request to https://www.motorsatwork.com/api/1.0/rest/test with HTTP basic access authentication using valid Motors@Work credentials included in the request header.

If successful, you will receive a json response:

{% highlight json%}
  {"message":"Way to go, you are authenticated!"}
{% endhighlight %}

If not successful, the response will look like this:
{% highlight json%}
  {"errors":{"entity":{"errorMessages":["Authorization failure."]}},"data":""}
{% endhighlight %}

[Java Example](/api-overview-java-authentication/)

#### <a name="Adding a measurement"></a> Adding a measurement
Test your Motors@Work Adding a Measurement by sending a PUT request to https://www.app.motorsatwork.com//api/1.0/rest/motor/external/measurement with HTTP basic access authentication using valid Motors@Work credentials included in the request header.

The PUT Request will have the following format
{% highlight json%}
  {
  "data": [
    {
  "referenceNumber": "MOTORTEST3",
  "measurementDate": "2017-04-05T12:37:53.000Z",
  "voltageAB": 450,
  "voltageBC": 400,
  "voltageCA": 380,
  "currentA": 5,
  "currentB": 6,
  "currentC": 7,
  "powerFactor": 90,
   "measuredSpeed": 1800,
   "powerDraw": 50,
   "totalHarmonicDistortion": 10,
   "insulationResistance": 20,
   "vibration": 20,
   "surgeMotorCircuit": 10 
   
	}
  ]
}
{% endhighlight %}

