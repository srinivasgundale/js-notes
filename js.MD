# JS important Notes

# Loading JS from externalfile 
When there's a complex and business logics or big chunk of code invlove then best practice to store it in external javascript file, instead in the html page. Because when we use external javascript file the file gets cached by browser and wont load everytime.
When the js file is cached it reads from the cahed file. The improves page speed and performance

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
