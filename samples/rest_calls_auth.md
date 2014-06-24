---
layout: samples
title: Authorization
icon: fa-phone-square
group: simple
---

REST Call with Authorization Header
===

Most of the RESTfull services playing role as remote APIs require some kind of authentication. In the following example we use *Basic* scheme with authorization header as it specified at [RFC 2617](https://www.ietf.org/rfc/rfc2617.txt). The target service could be OData service, from which we explicitly ask for JSON format as well.
 
Create a *Project* *Authorization* and a *JavaScript* service *rest_call_authorization.js* with the following content:

*GET Call*
<pre><code>var ioLib = require('io');

var url = 'http://rest.call/example';
var user = 'user1';
var password = 'secret1';

var getRequest = http.createGet(url);
var httpClient = http.createHttpClient(true);
var credentials = http.createUsernamePasswordCredentials(user, password);    
var scheme = http.createBasicScheme();
var authorizationHeader = scheme.authenticate(credentials, getRequest);
getRequest.addHeader(http.createBasicHeader("Accept", "application/json"));
getRequest.addHeader(authorizationHeader);
    
var httpResponse = httpClient.execute(getRequest);
    
var entity = httpResponse.getEntity();
var content = entity.getContent();
    
var input = ioLib.read(content);
http.consume(entity);

response.getWriter().println(input);
</code></pre>

For more information check the *[API](../help/api.html)* documentation