---
layout: samples
title: Thread
icon: fa-caret-right
group: simple
---

{{ page.title }}
===

Version 2.x
---

### Develop


1. Create a new project and name it **thread_basic**.
2. Select the *ScriptingServices* sub-folder of the project and open the pop-up menu.
3. Choose *New* -> *Scripting Service*.
4. Choose **Server-Side JavaScript Service** from the list of available templates.
5. Give it a meaningful name (e.g **thread_basic.js**).
6. Replace the generated code in **thread_basic .js** with the following:

```javascript

	/* globals $ */
	/* eslint-env node, dirigible */

	var threads = require('core/threads');
	var response = require('net/http/response');

	response.setContentType("text/plain; charset=UTF-8");

	// Define a JavaScript function
	function runnable() {
		response.println("Hello World from a Thread!");
	};

	// Pass a JavaScript function
	var worker = threads.create(runnable, "I am a thread");
	response.println(worker.getName());
	worker.start();
	worker.join(); // to be able to print to the response

	response.flush();
	response.close();
	
```

<div class="btn-toolbar pull-right">
	<a class="btn btn-warning" href="http://dirigible.eclipse.org/services/web/registry/anonymous.html?git=https://github.com/dirigiblelabs/sample_threads_thread_basic.git">Run</a>
	<a class="btn btn-info" href="http://www.dirigible.io/api/threads.html">API</a>
</div>

### Discover

To discover all available services, you can go to the [Registry](../help/registry.html).

1. From the main menu, choose **Window** -> **Show Perspective** -> **Registry**.
2. The **Registry** perspective represents a view to the enabled runtime content. From its menu, choose **Discover** -> **JavaScript** to open the currently available server-side JavaScript service endpoints.
3. You can see the list of available endpoints, where you can find yours by naming convention: **{project}/{service path}**
