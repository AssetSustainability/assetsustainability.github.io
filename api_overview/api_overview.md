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
| /api/1.0/rest/motor/external/measurement                      | PUT           | [Adding a measurement](#Adding a measurement)      |

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

###### Request 

The PUT Request will have the following format. The JSON Object is an array and can receive multiple readings in a single request. 

{% highlight json%}
 {
  "data": [
    {
  "referenceNumber": "OWASA - WTUL9215MO",
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
   
	},
	 {
  "referenceNumber": "OWASA - WTUL9215MO",
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

###### Request Mapping

| API Field                                                     | M@W Field[Screen\Tab\Field]     |  
| ------------------------------------------------------------- |:-------------:|  
| referenceNumber                                           	| My Motors \ Edit Details \ Reference Number            |  
| measurementDate                     				| My Motors \ Measurements \ Date           |  
| voltageAB                     				| My Motors \ Measurements \ Voltage AB           |  
| voltageBC                     				| My Motors \ Measurements \ Voltage BC           |  
| voltageCA                     				| My Motors \ Measurements \ Voltage CA           |  
| currentA	                     				| My Motors \ Measurements \ Current A           |  
| currentB	                     				| My Motors \ Measurements \ Current B           |  
| currentC	                     				| My Motors \ Measurements \ Current C           |  
| powerFactor                     				| My Motors \ Measurements \ Power Facor(%)           |  
| measuredSpeed                     				| My Motors \ Measurements \ Measured Speed           |
| powerDraw                     				| My Motors \ Measurements \ Power Draw           |
| totalHarmonicDistortion                			| My Motors \ Measurements \ THD           |
| insulationResistance                     			| My Motors \ Measurements \ Insulation Resistance           |
| vibration		                     			| My Motors \ Measurements \ Vibration (in\sec)           |
| surgeMotorCircuit                     			| My Motors \ Measurements \ Surge /Motor Circuit(%)           |

###### Response if Succesful

The UUID Retruned is the internal measurement ID that was created for your reference.

{% highlight json%}
  {"results":[{"id":"d9ffde38-a449-4b71-8bd8-1a9697786afd"},{"id":"47183416-28fa-4859-a706-a8b67bfbeae1"}]}
{% endhighlight %}

###### Response if Error

{% highlight json%}
  {"results":[{"errors":{"entity":{"errorMessages":["Could not find a matching record."]}},"data":""}]}
{% endhighlight %}



