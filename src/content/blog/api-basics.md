---
author: Kaushik Chemburkar
pubDatetime: 2023-05-18T14:27:00+11:00
title: API Basics
postSlug: api-basics
featured: false
draft: false
tags:
  - api
ogImage: ""
description:
  Simple ways to use APIs
---

I would like to show a quick way to apply a basic and fun API feature on your website.

You can browse through the [list of Public APIs](https://github.com/public-apis/public-apis) to find an API that you want to use.

For keeping it simple, I will be using the [Dog Facts API](https://kinduff.github.io/dog-api/). This API returns a random dog fact in JSON format.

**Step 1:** Go to [JSFiddle](https://jsfiddle.net/) and paste the following code:

**Step 2:** Paste the following code in the HTML and JavaScript section and read the comments in the code for more information. You may edit the code to suit your needs.

**`index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Random Dog Facts</title>
</head>
<body>
    <div id="dashboard">
        <!-- The data will be appended here -->
    </div>
    <button id="loadData">Load a Random Dog Fact</button>

    <!-- Include the JavaScript file -->
    <script src="main.js"></script>
</body>
</html>
```

**`main.js`**

```js
document.getElementById('loadData').addEventListener('click', function() {
    fetch('https://dogapi.dog/api/v2/facts')
    .then(response => response.json())
    .then(data => {
        // Clear the dashboard for each new set of facts
        document.getElementById('dashboard').innerHTML = '';

        // Access the data
        let facts = data.data; // This will get the array of fact objects

        // Loop through the array of facts
        for(let fact of facts) {
          // Access the body of the attributes for each fact
          let value = fact.attributes.body;

          // Create HTML elements
          let element = document.createElement('p'); // this creates a <p> element
          element.textContent = value; // this sets the text of the <p> element to your value

          // Add elements to the DOM
          document.getElementById('dashboard').appendChild(element); // this adds the <p> element to your dashboard div
        }

        // You can add code here to update HTML elements when new data comes in
    });
});
```

**Step 3:** Press the Run or `⌘+Enter` then press the "Load a Random Dog Fact" button on the preview window and you should see a random dog fact appear on the screen. You can press the button again to get a new fact.

With api access you can display the data, store, sort, filter it, combine with other apis and perform calculations to update the DOM.
