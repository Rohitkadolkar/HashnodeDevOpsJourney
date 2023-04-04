---
title: "#Day15: Python Libraries for DevOps #90DaysofDevOps"
datePublished: Tue Apr 04 2023 17:00:54 GMT+0000 (Coordinated Universal Time)
cuid: clg2ib9ur000409l9bn857nga
slug: day15-python-libraries-for-devops-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680627404834/2fc4597b-3c78-4b05-b78f-c957e90d38ce.jpeg
tags: python, json, devops, yaml

---

## Tasks

### Create a Dictionary in Python and write it to a json File.

**Create a file dict.py**

`touch dict.py`

**Open vim and type following code**

```python
import json

my_dict = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

with open("my_dict.json", "w") as file:
    json.dump(my_dict, file)
```

**Run the following .py file using:**

`python3 dict.py`

**Check using ls**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680614633143/6bfae7d8-4f27-4047-938a-3d45c2b2bbcc.png align="left")

**Verify by opening it**

`vim my_dict.json`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680620248616/d1a490d7-3578-4cf3-b8ac-e08d90dac00e.png align="center")

### Task2: **Read a json file** `services.json` **kept in this folder and print the service names of every cloud service provider.**

```python
output

aws : ec2
azure : VM
gcp : compute engine

```

**Step 1:**

**Create a file services.json**

```yaml
[
  {
    "name": "aws",
    "services": "ec2"
  },
  {
    "name": "azure",
    "services": "VM"
  },
  {
    "name": "gcp",
    "services": "compute engine"
  }
]
```

**Step 2:**

**Create a new file called clouds.py and write the code into it.**

```python
import json

# Read the JSON data from the file
with open('services.json') as f:
    data = json.load(f)

# Print the service names for each cloud service provider
for provider in data:
    print(provider['name'], ':', provider['services'])
```

**Now run it with python, it will give us the content in json file**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680618089241/685e7da1-8b30-4bd6-af23-eccb1d7b8cd3.png align="left")

### **Task3: Read YAML file using python, file** `services.yaml` **and read the contents to convert yaml to json**

**Step1**

**Create a file service.yaml**

**vim service.yaml**

**Add the following data in it:**

```yaml
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

**Step 2:**

**Create a file conversion.py and type the following code:**

```python
import json
import yaml

with open('service.yaml', 'r') as f:
    data = yaml.load(f, Loader=yaml.Safeloader)
with open('provider.json', 'w') as f:
    json.dump(data, f, sort_keys=False)
```

**Step 3:**

`run python3 conversion.py`

**File provider.json is created -**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680626940639/90f6d8c7-fa20-4fe0-b395-df43ce0ab227.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680626987503/2a1be7f0-35d0-4c1a-bb74-e8c7bf00c53d.png align="center")

**Congratulations! you are done with the tasks!**