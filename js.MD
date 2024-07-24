


### JS important Notes
<details>
<summary>External scripts</summary>

If we have a lot of JavaScript code, we can put it into a separate file.

Script files are attached to HTML with the src attribute:

```
<script src="/path/to/script.js"></script>
Here, /path/to/script.js is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, src="script.js", just like src="./script.js", would mean a file "script.js" in the current folder.
```
We can give a full URL as well. For instance:
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
To attach several scripts, use multiple tags:

<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
```

### Please note:
As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files.

The benefit of a separate file is that the browser will download it and store it in its cache.

Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once.

That reduces traffic and makes pages faster.

If src is set, the script content is ignored.
A single <script> tag can’t have both the src attribute and code inside.

This won’t work:
```
<script src="file.js">
  alert(1); // the content is ignored, because src is set
</script>
```
We must choose either an external <script src="…"> or a regular <script> with code.

The example above can be split into two scripts to work:
```
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
</details>
# Use hotkeys for comments!
In most editors, a line of code can be commented out by pressing the Ctrl+/ hotkey for a single-line comment and something like Ctrl+Shift+/ – for multiline comments (select a piece of code and press the hotkey). For Mac, try Cmd instead of Ctrl and Option instead of Shift.

Nested comments are not supported!
There may not be /*...*/ inside another /*...*/.

Such code will die with an error:

```
/*
  /* nested comment ?!? */
*/
alert( 'World' );
```
