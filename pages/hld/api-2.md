---
title: GET /pet/findByStatus
sidebar: mydoc_sidebar
permalink: api_2.html
folder: petstore
toc: false
swaggerfile: petstore
swaggerkey: /pet/findByStatus
method: get
---

## Description

{% include swagger_parsers/getattribute.md attribute="summary" %}

{% include swagger_parsers/getattribute.md attribute="description" %}

## Path parameters

{% include swagger_parsers/getparams.md paramtype="path" %}

## Query parameters

{% include swagger_parsers/getparams.md paramtype="query" %}

## Responses

{% include swagger_parsers/getresponses.md %}

Content types:

{% include swagger_parsers/getattribute.md attribute="produces" type="list" %}

## Examples
<ul id="profileTabs" class="nav nav-tabs">
    <li class="active"><a href="#python" data-toggle="tab">Python</a></li>
    <li><a href="#postman" data-toggle="tab">Postman</a></li>
    <li><a href="#curl" data-toggle="tab">cURL</a></li>
</ul>

<div class="tab-content">

<div role="tabpanel" class="tab-pane active" id="python">
<p>The example below shows how to request all pets listed as <code>available</code>. You'll need to install the <a href="http://docs.python-requests.org/en/master/user/quickstart/"> Requests</a> library into your virtual environment (<code>pip install requests</code>).</p>

<pre class="highlight">
<code>import requests
import json

url = 'http://petstore.swagger.io/v2/pet/findByStatus?status=available'
response = requests.get(url).json()</code>
</pre>

<p>To display the first three results:</p>

<pre class="highlight">
<code>>>> response[:3]
[{'id': 1116,
  'category': {'id': 0, 'name': 'string'},
  'name': 'doggie',
  'photoUrls': ['string'],
  'tags': [{'id': 0, 'name': 'string'}],
  'status': 'available'},
 {'id': 1427504384,
  'name': 'Fido',
  'photoUrls': [],
  'tags': [],
  'status': 'available'},
 {'id': 1427504385,
  'category': {'id': 0, 'name': 'Lions'},
  'name': 'Simba',
  'photoUrls': ['Simba-photo'],
  'tags': [{'id': 0, 'name': 'Sarko'}],
  'status': 'available'}]</code>
</pre>
</div>

<div role="tabpanel" class="tab-pane" id="postman">
<ol>
<li>In Postman, enter the URL:<br><code>http://petstore.swagger.io/v2/pet/findByStatus?status=available</code></li>
<li>When you execute the request, the response body will look something like this:
   {% include image.html file="postman.png" max-width="780" %}
</li>
</ol>
</div>

<div role="tabpanel" class="tab-pane" id="curl">
<pre class="highlight">
<code>curl -X GET "http://petstore.swagger.io/v2/pet/findByStatus?status=available" -H "accept: application/json" | python -m json.tool

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 3446k    0 3446k    0     0  5989k      0 --:--:-- --:--:-- --:--:-- 5983k
[
    {
        "category": {
            "id": 0,
            "name": "string"
        },
        "id": 1116,
        "name": "doggie",
        "photoUrls": [
            "string"
        ],
        "status": "available",
        "tags": [
            {
                "id": 0,
                "name": "string"
            }
        ]
    },
    {
        "id": 1427504384,
        "name": "Fido",
        "photoUrls": [],
        "status": "available",
        "tags": []
    },
    ...
</code>
</pre>
</div>
</div>

{% include links.html %}
