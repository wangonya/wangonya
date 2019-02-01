---

title: "Displaying a css spinner on ajax calls with fetch api"
date: "2019-02-01T08:18:26+03:00"
description: "How to show a loader when getting or posting data with fetch api"
tags: [javascript, css]

---

I always have to search for how to do this or refer back to my previous code whenever I work with `fetch`. For a while, I've used the solution to [this](https://stackoverflow.com/questions/43792026/display-spinner-during-ajax-call-when-using-fetch-api) SO question. It's a correct solution and it works great but to be honest, I couldn't really explain _very well_ what was going on if someone asked me to explain that piece of my code. So I thought of a simple way to do it. It's very simple really, I think I was just overthinking it. Here's how:

## Setting up the HTML

```html
<!-- this will show our spinner -->
<div id="spinner"></div>

<!-- And this will fetch our data -->
<button onclick="fetchData()">Load data</button>
```

## Creating the CSS spinner

```css
#spinner {
  visibility: hidden;
  width: 80px;
  height: 80px;

  border: 2px solid #f3f3f3;
  border-top: 3px solid #f25a41;
  border-radius: 100%;

  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;

  animation: spin 1s infinite linear;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

#spinner.show {
  visibility: visible;
}
```

The spinner visibility is hidden by default. This is the element we'll manipulate in order to show and hide it as desired.

## Getting things working with Javascript

I'll use the [random user generator api](https://randomuser.me/).

```javascript
const spinner = document.getElementById("spinner");

function showSpinner() {
  spinner.className = "show";
  setTimeout(() => {
    spinner.className = spinner.className.replace("show", "");
  }, 5000);
}

// function hideSpinner() {
//   spinner.className = spinner.className.replace("show", "");
// }

function loadData() {
  showSpinner();
  fetch("https://randomuser.me/api/")
    .then(response => response.json())
    .then(data => {
      // hideSpinner()
      console.log(data);
    });
}
```

When `showSpinner()` is called, it adds a `show` class to the `spinner` element, which turns the `visibility: visible` as we specified in the css. To hide the spinner, the `show` class is removed which turns the `visibility: hidden`.

For demonstration purposes, I've used a timeout function and set it to 5 seconds so the spinner can load since fetching the data takes like 1 second. But ideally, you'd want to have a `hideSpinner()` function and call that after the data has been returned. Then, the timeout time should be increased to maybe 15 seconds since you don't want it to load forever, after which you'd show an error.

Here's the [pen](https://codepen.io/wang0nya/pen/bzwQPr)
