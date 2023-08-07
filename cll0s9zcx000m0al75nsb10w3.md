---
title: "Day 15  Python Libraries for DevOps"
datePublished: Mon Aug 07 2023 11:22:50 GMT+0000 (Coordinated Universal Time)
cuid: cll0s9zcx000m0al75nsb10w3
slug: day-15-python-libraries-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691407028920/e5933a30-07ef-40b4-b9f0-2955c0b4122a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691407274936/999efc1c-246d-4480-91a6-b6e9eb09be74.png
tags: python, devops, 2articles1week, 90daysofdevops-chanllenge

---

### **Introduction to JSON and YAML**

### **JSON:**

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON stands for JavaScript Object Notation.</div>
</div>

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON is easy for both humans to read and write and for machines to parse and generate.</div>
</div>

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON is primarily used in web development for transmitting data between a server and a web application as an alternative to XML.</div>
</div>

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON data is represented in key-value pairs, where the keys are strings, and the values can be of various data types, such as strings, numbers, booleans, arrays, and even other JSON objects.</div>
</div>

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON values cannot be functions or methods; they are meant to be data only.</div>
</div>

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON objects are enclosed in curly braces <code>{}</code>, and each key-value pair is separated by a colon <code>:</code>.</div>
</div>

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">JSON arrays are ordered lists of values, enclosed in square brackets <code>[]</code>, with each value separated by a comma</div>
</div>

### **YAML:**

Yaml is human readable data serialization language that is often used for writing the configuration file depending on whom you ask.

Yaml stands for yet another markup language or ain't markup language (a recursive acronym) which emphasizes that YAML is for data, not documents.

It is easy to read and understand

Yaml is used by the Ansible automation tool to create automation processes in the form of an Ansible playbook.

yaml file use a.yml or .yml extension. it supports JSON files.

It is simple to use and in the Python style. in the 3 dashes (---) is used to signal the start of a document and (...) is used to end the documents.

## **Tasks:**

1. Create a Dictionary in Python and write it to a JSON File.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691403975160/3bf0e7e4-d49e-482e-957f-53d76703f82c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691403997450/76bc7430-f369-4b85-91e1-f7a4478cf552.png align="center")

1. Read a JSON file `services.json` kept in this folder and print the service names of every cloud service provider.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691405316306/dec715ec-99d2-446f-8ec1-57a67f7cf7ee.png align="center")

first of all import module

```bash
import json
```

The code starts by importing the `json` module, which provides functions for working with JSON data in Python.

then store JSON data in string form

```bash
{
    "services": {
      "debug": "on",
      "aws": {
        "name": "EC2",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      },
      "azure": {
        "name": "VM",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      },
      "gcp": {
        "name": "Compute Engine",
        "type": "pay per hour",
        "instances": 500,
        "count": 500
      }
    }
  }
```

The JSON data is provided as a multi-line string, representing a JSON object with nested data.

Parsing JSON data into a Python dictionary:

```bash
data = json.loads(json_data)
```

Extracting service names from the dictionary:

```bash
 service_names = [data["services"][provider]["name"] for provider in data["services"] if provider != "debug"]
```

Printing the service names:

```bash
for service_name in service_names:
    print(service_name)
```

Finally, the code uses a `for` loop to iterate through the `service_names` list and print each service name one by one. The output will be the names of each cloud service provider's service, i.e., "EC2", "VM", and "Compute Engine".

1. Read YAML files using Python, file `services. yaml` and read the contents to convert yaml to json
    

import the modules

```bash
import yaml
import json
```

Define the yaml data.

```bash
---
services:
  debug: 'on'
  aws:
    name: EC2
    type: pay per hour
    instances: 500
    count: 500
  azure:
    name: VM
    type: pay per hour
    instances: 500
    count: 500
  gcp:
    name: Compute Engine
    type: pay per hour
    instances: 500
    count: 500
```

Load yaml data in the python

```bash
    data = yaml.safe_load(yaml_data)
```

convert the python dictionary in the JSON

```bash
    json_data = json.dumps(data, indent=4
```

now print the JSON data

```bash
    print(json_data)
```

📍 Conclusion.

Above mentioned information is much important for a DevOps engineer as he has you have completed the json and yaml mudule in explained about the json and the yaml and many more described the use of yaml .joining the ranks of legendary DevOps engineers! Embrace version control and collaboration, and your coding adventures shall know no bounds!

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**