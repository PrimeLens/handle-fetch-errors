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
    console.log('===>  ' + typeof response.status); // 'number'
    console.log('===>  ' + response.status);        // 400
    console.log('===>  ' + response.statusText);    // 'BAD REQUEST'
    // if text is sent with it
    response.text().then(text => {
      console.log('===>  ' + text);                 // custom text sent from back end
    });  
    // can detect cstom error codes written by back end
    if (response.status===432){
      // must pass in a string to Error, it yields and object
      throw new Error('Bad json');
    } else {
      // must pass in a string to Error, it yields and object
      throw new Error(response.statusText);
    }
  }
  return response;
})
.catch(errObj=>{
  // must pass in a string to Error, it yields and object
  // text appears in message property
  console.log(errObj.message);
});


```
