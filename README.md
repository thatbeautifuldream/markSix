# 📣 `levelZero-markSix`

## Minions Speak App

- 🍌 This is a project to translated text from English to Minion Speak 🍌

## Learings from this project

- There is a document object model (DOM) in JavaScript
- The document object has a property called `body` that has a property called `innerHTML` that has a property `textContent` that has a property `innerText`
- Likewise we can use this API to manipulate the DOM using JavaScript
- Lets see how we can use this API to manipulate the DOM using JavaScript, here in this project we select button using querySelector using its id and furthur we can set the textContent of the p tag using `innerText` or `innerHTML`, dont get into the specifics of the code now, just understand that we can manipulate the DOM using JavaScript.

```js
const log = console.log;

// URL Generator function just adds encoded string to the API endpoint
function urlGenerator(text) {
  return (
    "https://api.funtranslations.com/translate/minion.json" +
    "?" +
    "text=" +
    encodeURIComponent(text)
  );
}
// encodeURIComponent is used to encode the string to be sent to the API endpoint

var btnTranslate = document.querySelector("#btn-translate");
btnTranslate.addEventListener("click", clickHandler);

// clickHandler is the callback handler for the click event
function clickHandler() {
  var txtInput = document.querySelector("#text-input");
  log(txtInput.value);
  var res = urlGenerator(txtInput.value); // calls the urlGenerator function
  log(res); // logs the URL to the console

  // fetch API call
  // fetch() is a browser API that allows us to make HTTP requests
  // fetch() returns a promise
  // Promises are resolved or rejected based on the result of the asynchronous operation
  // fetch() returns a promise that resolves to a Response object using .then() method
  // Response object has a method called json() which returns a promise that resolves to a JSON object
  // We can use .then() method to access the JSON object
  // We can chain multiple .then() methods to access the JSON object
  // We can handle errors using .catch() method

  fetch(res)
    .then((response) => response.json())
    .then((json) => {
      var translatedText = json.contents.translated;
      log(translatedText);
      var outputPTag = document.querySelector("#output");
      outputPTag.innerText = translatedText;
    })
    .catch(function errorHandler() {
      log("error occured", error);
      alert("something wrong with server! try again after some time");
    });
}
```

- I have tried to explain the code above in a way that is easy to understand and understand the concepts in the comments.

## Contributing to this project (Mostly UI related)

- If you want to contribute to this project, please open an issue or create a pull request.
