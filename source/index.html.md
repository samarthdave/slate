---
title: ComputeDocs

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

TODOS:
- how to connect to the VPN
  - Cisco Anyconnect for Windows or MacOS
  - alternatively use openconnect for linux & macos
- setup VS Code for coding environment
  - use SSH fs for your environment
  - use git & github or some online service to keep track of projects

# Welcome

Hi! As students of Texas A&M University, we're given access to the central "Compute" service (which is hosted at compute.cse.tamu.edu). This site will help you set up your ssh connection and workflow to write your code and make sure that your compute isn't in your way.

# Overarching Steps
1. Connect to TAMU VPN ([connect.tamu.edu](https://connect.tamu.edu)) if you're not connected to campus wifi.
  - **Skip this step if you're on campus (connected to TAMU wifi)**
  - **MacOS & Linux**: Cisco AnyConnect or openconnect
  - **Windows**: Cisco Anyconnect
2. SSH into compute through some terminal program
  - **MacOS & Linux**: native Terminal Program or [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
  - **Windows**: [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) or PowerShell (yuck)
3. Set up a workflow (my set up is below).
4. Get coding ;)

# Windows Users

## Install VPN Client (Cisco Anyconnect recommended)
1. Go to [https://connect.tamu.edu](https://connect.tamu.edu).
2. Log in with NetID & password.
3. Install the "Cisco AnyConnect Secure Mobility Client" for Windows.
  - **Alternatively**, install AnyConnect from [Cisco's website](https://www.cisco.com/c/en/us/support/security/anyconnect-secure-mobility-client-v4-x/model.html#~tab-downloads).

## Connecting to TAMU VPN
**Skip this step if on campus (connect to TAMU wifi)**
1. Open Cisco Anyconnect.
2. In the prompt, type in `connect.tamu.edu` and press **Connect**.
3. Type in username (NetID) and password.
4. Approve sign in with [Duo Authentication](https://apps.apple.com/us/app/duo-mobile/id422663827).

## Connecting to Compute Services ("ssh" into compute)
1. Open PuTTY

# MacOS Users

## Steps
1. Open up your terminal app
```
Command + Space > "Terminal"
```

2. Enter the command ```ssh``` and you should get the output you see on the right side.

```bash
MacOS_user $ ssh # run "ssh" in the terminal
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

3. You're almost done! If you're on the A&M WiFi network (tamulink-wpa), skip to step 4. If you're not, you need to use A&M's VPN. This VPN will put you in College Station (actually on campus) and can be used for a myriad of purposes, including evading country firewalls (iMessage - Qatar, WhatsApp - China, etc.). But for now, let's use it to access the Compute servers.

**Here's how to connect to the A&M VPN** before you try step 4.



4. The last line of ssh help that you see is what we're going to use.

Go ahead and copy the line below. Be sure to replace the USERNAME with the handle that you use to login to A&M services. **Note, this is not your UIN.**

```bash
ssh USERNAME@compute.cs.tamu.edu
# "compute.cse.tamu.edu" does the same
```

```
The authenticity of host 'blah.blah.blah (10.10.10.10)' can't be established.
RSA key fingerprint is a4:d9:a4:d9:a4:d9a4:d9:a4:d9a4:d9a4:d9a4:d9a4:d9a4:d9.
Are you sure you want to continue connecting (yes/no)?
```


# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

