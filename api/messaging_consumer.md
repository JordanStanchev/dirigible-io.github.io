---
layout: api
title: Message Consumer
icon: fa-ellipsis-h
---

{{ page.title }}
===

The Messaging Consumer is an object which can send text messages to a Queue or Topic destination in the built-in Message Broker. This version is backed by the full fledged messaging broker [Apache ActiveMQ](http://activemq.apache.org/).

Version 3.x
---


- Module: **messaging/v3/consumer**
- Alias: **messaging/consumer**
- Definition: [https://github.com/eclipse/dirigible/issues/92](https://github.com/eclipse/dirigible/issues/92)
- Source: [/messaging/v3/consumer.js](https://github.com/dirigiblelabs/api-v3-messaging/blob/master/messaging/v3/consumer.js)
- Facade: [MessagingFacade](https://github.com/eclipse/dirigible/blob/master/api/api-facades/api-messaging/src/main/java/org/eclipse/dirigible/api/v3/messaging/MessagingFacade.java)
- Status: **alpha**


### Basic Usage

```javascript
var consumer = require('messaging/v3/consumer');
consumer.queue("queue1").receive(1000);
```

### Definition

#### Functions

---

Function     | Description | Returns
------------ | ----------- | --------
**queue()**   | Returns an object representing a Message Queue | *Queue*
**topic()**   | Returns an object representing a Message Topic | *Topic*


### Objects

---

#### Queue

Function     | Description | Returns
------------ | ----------- | --------
**receive(timeout)**   | Receives a message from this Message Queue if any or null with the given timeout | *string*


#### Topic

Function     | Description | Returns
------------ | ----------- | --------
**receive(timeout)**   | Receives a message from this Message Topic if any or null with the given timeout | *string*



### Compatibility

Rhino | Nashorn | V8
----- | ------- | --------
 ✅  | ✅  | ✅
