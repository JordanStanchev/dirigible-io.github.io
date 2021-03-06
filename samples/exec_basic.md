---
layout: samples
title: Exec
icon: fa-caret-right
group: simple
---

{{ page.title }}
===

Version 2.x
---

### Develop


1. Create a new project and name it **exec_basic**.
2. Select the *ScriptingServices* sub-folder of the project and open the pop-up menu.
3. Choose *New* -> *Scripting Service*.
4. Choose **Server-Side JavaScript Service** from the list of available templates.
5. Give it a meaningful name (e.g **exec_basic.js**).
6. Replace the generated code in **exec_basic.js** with the following:

```javascript

	/* globals $ */
	/* eslint-env node, dirigible */

	var exec = require('service/exec');
	var response = require('net/http/response');

	var context = {"input_param": "input_param_value"};

	// Test execution
	var result = exec.test("/service/exec_target_basic.js", context);

	response.println("Printing output parameter: " + result.context.output_param);

	// use also exec.js(), exec.flow(), exec.job(), exec.sql(), exec.command() ...

	response.flush();
	response.close();
	
```

After creating the above file:

1. Select the *ScriptingServices* sub-folder of the project and open the pop-up menu.
2. Choose *New* -> *Scripting Service*.
3. Choose **Server-Side JavaScript Service** from the list of available templates.
4. Give it a meaningful name (e.g **exec_target_basic.js**).
5. Replace the generated code in **exec_target_basic.js** with the following:

```javascript

	/* globals $ */
	/* eslint-env node, dirigible */

	var context = require('core/context');
	var response = require('net/http/response');

	// print in the response
	response.setContentType("text/html; charset=UTF-8");
	response.setCharacterEncoding("UTF-8");
	response.println("Entering target...");
	var input_param = context.get("input_param");
	response.println("Printing input parameter: " + input_param);
	response.println("Setting output parameter");
	context.set("output_param", "output_param_value");
	response.println("Exiting target...");



	// do not close the response, if you plan to use it further
	//response.flush();
	//response.close();
	
```

<div class="btn-toolbar pull-right">
	<a class="btn btn-warning" href="http://dirigible.eclipse.org/services/web/registry/anonymous.html?git=https://github.com/dirigiblelabs/sample_service_exec_basic.git">Run</a>
	<a class="btn btn-info" href="http://www.dirigible.io/api/exec.html">API</a>
</div>

### Discover

To discover all available services, you can go to the [Registry](../help/registry.html).

1. From the main menu, choose **Window** -> **Show Perspective** -> **Registry**.
2. The **Registry** perspective represents a view to the enabled runtime content. From its menu, choose **Discover** -> **JavaScript** to open the currently available server-side JavaScript service endpoints.
3. You can see the list of available endpoints, where you can find yours by naming convention: **{project}/{service path}**
