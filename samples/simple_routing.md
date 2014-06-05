---
layout: help
title: Samples - Routing
icon: fa-gift
---

Simple Routing
===

The simplest *Integration Service* you can have is the one using the built in conditioning DSL of [Apache Camel|http://camel.apache.org].
General steps are valid for all the other template types for the different integration patterns.

Create a simple project named *routing* (from main menu New->Project)
Select just created project in the Workspace Explorer. From the pop-up menu select *New->Integration Service*

![Content Based Routing 1](bookstore/108_content_based_routing_1.png)

From the template list in the wizard which is opened, chose "Content Based Routing by Header Parameter"

![Content Based Routing 2](bookstore/109_content_based_routing_2.png)

Click Next and give a name of the routes artifact - *simple_routing.routes*

![Content Based Routing 3](bookstore/110_content_based_routing_3.png)

On the next page enter the required parameters for this particular template:

> Route Identifier: *simple_routing*
> Endpoint Address: *simple_routing_endpoint*
> Condition Parameter Name: *name_parameter*

![Content Based Routing 4](bookstore/111_content_based_routing_4.png)

Click finish and inspect the generated artifact, which should look like this:

<pre><code>< routes xmlns="http://camel.apache.org/schema/spring">
    < route id="simple_routing">
        < from uri="servlet:///simple_routing_endpoint" />
        < choice>
            < when>
                < header>name_parameter</header>
                < transform>
                    < simple>Hello ${header.name_parameter} how are you?</simple>
                < /transform>
            < /when>
            < otherwise>
                < transform>
                    < constant>Add a name parameter to uri, eg ?name_parameter=foo</constant>
                < /transform>
            < /otherwise>
        < /choice>
    < /route>
< /routes>
</code></pre>

[Activate](../help/activation.html) or [publish](../help/publishing.html) the project and it is done.

Go to location *http //[host]:[port]/dirigible/camel/simple_routing_endpoint* and try it.

The pattern which is used for generating the location URL can be found [here](../help/integration_services.html)
