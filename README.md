# handle-fetch-errors
handling errors with Fetch API



```

// establish the request object
var reqObj = {}
reqObj.headers = new Headers({'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8'});
reqObj.method = 'GET';
reqObj.body = (typeof payload !== 'string') ? JSON.stringify(payload) : payload;
// fire up the promise
var request = new Request(finalURL, reqObj);
var fPointer = fetch(request)
.then(response => {
  if (!response.ok) {
    throw Error(response.statusText, response);
  }
  return response;
})
.catch((errText, response)=>{
  console.log('===>  ', errText);
  console.log('===>  ' + typeof response.status);
  console.log('===>  ' + response.status);
  console.log('===>  ' + response.statusText);
  // if text is sent with it
  response.text().then(text => {
    console.log('===>  ' + text);
  });
});


```
