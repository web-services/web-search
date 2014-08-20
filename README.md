Web Search
======

Search is arguably the most common feature found across all types of apps. Whether it manifests itself in visual UI as an input with a submit button, or a query that is collected and transmitted in code, search and data presentation from multiple sources is what dirves many of today's most compelling app experiences.

The problem is that search and retrieval of data from multiple and external sources is still cumbersome. After the introduction of `XMLHttpRequest` and `JSON`, there's been almost zero platform advancement in the area of services. Some platform folks would tell you, _"It's all there, AJAX, JSON, Cross Domain XHR - what's the big deal"_. But any developer who has had to interact with even the most common services knows the experience could be better, easier, faster, and more ergonomic.

This service standard sets out to remove barriers, streamline use-cases, and make search a truly effortless activity for developers. Let's take a look at how it works:

```

// Create and configure a [WebSearch Object] instance

var mySearch = new WebSearch(['www.target.com', 'www.zazzle.com'], {
  query: 'red t-shirt',
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

// Fetch results using the current parameters
// and state of the [WebSearch Object]

mySearch.fetch();

```

