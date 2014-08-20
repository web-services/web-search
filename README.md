Web Search
======

Search is arguably the most common feature found across all types of apps. Whether it manifests itself in visual UI as an input with a submit button, or a query that is collected and transmitted in code, search and data presentation from multiple sources is what dirves many of today's most compelling app experiences.

The problem is that search and retrieval of data from multiple and external sources is still cumbersome. After the introduction of `XMLHttpRequest` and `JSON`, there's been almost zero platform advancement in the area of services. Some platform folks would tell you, _"It's all there, AJAX, JSON, Cross Domain XHR - what's the big deal"_. But any developer who has had to interact with even the most common services knows the experience could be better, easier, faster, and more ergonomic.

### Client Interface

This service standard sets out to remove barriers, streamline use-cases, and make search a truly effortless activity for developers. Let's take a look at the DOM version of the interface:

```javascript

// Create and configure a [WebSearch Object] instance

var mySearch = new WebSearch(['www.target.com', 'www.zazzle.com'], {
  context: 'product',
  query: 'red shirt',
  skip: 0,
  take: 20
});

// Add callbacks to the instance of [WebSearch Object]

mySearch.onsuccess = function(results){
  for (var z in results){
    results[z].forEach(function(result){
      
    });
  }
};

mySearch.onerror = function(error){
  
};

// Fetch results using the current parameters and state
// of the [WebSearch Object]. The parameters below would
// be used to fetch from a new skip and take position.
// Use of the parameters updates the object's skip/take values.

mySearch.fetch(skip, take);

// Fetches the next set of results based on the
// current skip/take values of the [WebSearch Object].
// The object's skip value automatically advanced.

mySearch.next();

// Fetches the previous set of results based on the
// current skip/take values of the [WebSearch Object]
// The object's skip value automatically decremented.

mySearch.previous();

```

### How It Works

It is helpful to understand how the system works. In the following section, we'll explore the steps the UA takes in processing, dispatching, and returning results. There are 4 important proceedures in the system that allow for the API to work.

##### 1. Fetch and verify `services.json`

The first step the User Agent performs, is to fetch the `services.json` file(s) from the root of the domains passed into the WebSearch object instantiation. If the JSON descriptor file is located, and contains a `search` object with a `url` endpoint value, it caches this endpoint as the target for WebSearch requests. This only happens if this leg of the journey has never been performed for the requesting domain, or if the cache period for the file has expired.

##### 2. 

##### 3. Create and dispatch requests

Once the UA has determined a URL location for each domain's search requests, it dispatches one request for each domain provided. These requests are cross-domain allowed by default, as the presence of the `services.json` file acts as a directive to the UA to allow cross-origin requests to the specified search service endpoint.

##### 4. Domain packaging and returns

Domains recieve the standard request payload from the WebSearch invocation, and return their results as an array of results
