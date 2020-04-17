no_breadcrumb:true

# Tasks JavaScript Quick Start

Welcome to the Engage Platform. In this Quick Start, we are going to help you get a list of tasks that can be assigned to agents within your account. Obtaining a reference to a task by its ID is an important first step in managing the workflow of that task. This Quick Start will have you up and running in minutes.

## Obtain Access Key

The first thing you need to do is obtain an API Access Token if you do not already have one. Access tokens can be created and/or accessed via the "API access token" area in the "Admin" area of your Engage portal.

??? tip "How to generate an Engage API access token"

    1. Login to your Engage portal and click on the "Admin" menu located in the top, horizontal menu.

    2. Select "API access tokens" towards the bottom of the left hand menu.

    3. You should see a list of access tokens if any have been provisioned. Select the token, or click the "+" button to create a new one.

    4. Finally, enter a label/description for your token, and select an Agent on which the token will act on behalf of. Make sure the token is "enabled" and click "Save."

          ![API access token](../../../img/api-token.png)

Make note of the access token generated as you will need it later.

## Create and Edit tasks.js

Create a file called `tasks.js`. Be sure to edit the variables in &lt;ALL CAPS&gt; with your app's credentials.

```javascript
var https = require('https')

const SERVER = '<YOUR-DOMAIN>.api.engagement.dimelo.com'
const ACCESS_TOKEN = '<API-ACCESS-TOKEN>'
const API = "/1.0/tasks"

var headers = {
        'Authorization': "Bearer " + ACCESS_TOKEN
    }

var options = {host: SERVER, path: API, method: 'GET', headers: headers};

var get_req = https.get(options, function(res) {
      var response = ""
      res.on('data', function (chunk) {
          response += chunk
        }).on("end", function(){
          if (res.statusCode == 200)
            console.log(response)
          else
            console.log(res.statusCode)
        });
    }).on('error', function(e) {
          console.log(e.message)
    });
```

### Run Your Code

You are almost done. Now run your script.

```bash
$ node tasks.js
```

## Need Help?

Having difficulty? Feeling frustrated? Receiving an error you don't understand? Our community is here to help and may already have found an answer. Search our community forums, and if you don't find an answer please ask!

<a target="_new" href="https://forums.developers.ringcentral.com/search.html?c=72&includeChildren=true&f=&type=question+OR+kbentry+OR+topic&redirect=search%2Fsearch&sort=newest&q=interactions">Search the forums &raquo;</a>

## What's Next?

When you have successfully made your first API call, it is time to take your next step towards building a more robust Engage application.

<a class="btn btn-success btn-lg" href="https://developers.ringcentral.com/engage/api-reference/">Explore the REST API &raquo;</a>
