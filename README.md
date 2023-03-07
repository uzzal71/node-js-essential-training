# Nodejs Essential Training
#### 1. Inspecting the global object
```
console.log("Hello World")
```
node global.js OR node global run your terminal
```
let hello = "Hello World from Node.js";
let justNode = hello.slice(17);
console.log(`Who let the ${justNode} out?`);
```
In the browser, the global object is called the window. But in Node.js, the global object is called global. Let's take a look at this global Node.js object. So here is what is available to us within Node.js, these classes, objects, and functions. We don't need to import them to use them. They're scoped to the global namespace, which means we can access them at any time. So over here in our file, which is called global.js, we want to make sure that we can console.log as we expect to, and I feel like we can. (laughs) So let's go ahead and console.log a Hello World. All we need to do to run this file is we'll open up our terminal. We can hit Control + Backtick. We want to make sure we're navigated to the right directory. I'll type cd, I'll drag my start folder over the terminal and hit Enter. And now I should be able to run the file. So we can type node global.js, and this will console.log Hello World. So the console object is a part of the global namespace. So I could say global.console.log, and our results would be exactly the same. So let's remove this. We're going to try to run this again, but this time, and again, we can always hit up, the up arrow, to get the last command that we used. I'm going to remove the .js from this command. And we'll see that this is going to infer that this is a JavaScript file that can be run, and it'll run it accordingly. So Node.js will assume that that's a JavaScript file. We want to think about the global object in Node as being a bit like the window object in the browser. I said "a bit like the window object" though because there are some differences. So let's go ahead and create a variable. And this string will be called hello. We'll say Hello World from Node.js. And now we can console.log global.hello. Now if the global object was exactly like the window object, we should be able to do this. But this is going to actually log undefined because the variables are scoped to this file or this module. So that means that every new file that we create will have its own scope for these variables. So let's get rid of that. It's too wordy anyway. Now if we node global, we can see the contents of that string. So we can use JavaScript in this file because Node.js uses Chrome's V8 interpreter. Node.js works with primitives, objects, arrays, and functions, just like your browser does. So we could do something like this. We could say let justNode = hello.slice. And what we'll see here if we console.log justNode, this is going to slice our string at position 17. So it'll get everything after that. The function that we're used to from JavaScript works in much the same way. So we also could do something like this, where we inject a variable into a string. So console.log, Who let the justNode out. We're using a template string here. Notice these are backticks, which you'll find in the upper left-hand corner of your keyboard. We use the template string here. We're using the dollar sign and the curly braces to take whatever this value is and inject it right here into the string. So running this again, we should see this new string has been created. So we want to think about the global object as containing all of the objects, values, and methods that we can use in a Node.js file without having to import anything. For the rest of this chapter, we're going to explore what else is available to us globally in Node.js.
