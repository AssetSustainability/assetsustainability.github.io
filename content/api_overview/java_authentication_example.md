---
title: Motors@Work API Overview - Java Authentication Example
layout: helpfile
categories: ['api']
permalink: api-overview-java-authentication/
sequence: 2
tags:
- api
---

##Send a request to Motors@Work, Java example

The following codes shows how to call the Motors@Work authentication endpoint using Java and basic authentication.
{% highlight java%}
    private void sendGet(String user, String password) throws Exception {
        String userEncryption = String.format("%s:%s",user,password);
        userEncryption="Basic "+Base64.getEncoder()
            .encodeToString(userEncryption.getBytes());

        String url = "https://www.motorsatwork.com/api/1.0/rest/test";

        URL obj = new URL(url);
        HttpURLConnection con = (HttpURLConnection) obj.openConnection();
        con.setRequestMethod("GET");

        //add request header
        con.setRequestProperty("Authorization", userEncryption);

        int responseCode = con.getResponseCode();
        System.out.println("\nSending 'GET' request to URL : " + url);
        System.out.println("Response Code : " + responseCode);

        BufferedReader in = new BufferedReader(
            new InputStreamReader(con.getInputStream()));
        String inputLine;
        StringBuffer response = new StringBuffer();

        while ((inputLine = in.readLine()) != null) {
            response.append(inputLine);
        }
        in.close();

        //print result
        System.out.println(response.toString());

    }
{% endhighlight %}
