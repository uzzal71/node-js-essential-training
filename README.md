# Nodejs Essential Training
#### 2.1 Inspecting the global object
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

#### 2.2 Using the require function
So what else do we have globally available to us in Node.js? Well, we have some references to the current file and the current directory. So let's replace this with a few console.log messages. Remember, console.log is available to us globally without having to import anything. So we want to log the __dirname and the __filename. We also want to make sure that we're in the right folder. So we will make sure that we're navigated correctly, typing cd, dragging that file directory over. And then we're going to say node global. So now this is going to point directly at the directory where the file is located and then directly at the file. So notice that the filename variable includes the entire path. So also available to us globally is the common.js module pattern. So this is the pattern we're going to use to import other code into our files. One way that we can import these other modules is we can use this function.
```
console.log(__dirname);
console.log(__filename);
```
 First things first, we're going to import it and this typically happens at the top of the file. So we're going to import the path module from Node. Now, the path module is one of those core modules that's part of Node.js but in order to use it, we have to import it for us to be able to use all of these functions. So why might I want to use one of these functions? Well, I want to pull out just global.js from the file extension that we're getting from the filename variable. So the way that I can do that is we can use another template string. We'll say the file name is. We will use the template string here. And instead of just wrapping this around the filename, what we actually want to say is path.basename. And this is a function that's going to take in that filename as an argument. We also want to make sure to close this string. So we're opening it up with a back tick and closing it with a back tick. So when I hit save there, we should be able to run this again. Node global and check it out, we've plucked this from that string using this function. Any time we need to do any parsing of path values, we can use these functions.
```
const path = require("path");

console.log(__dirname);
console.log(
  `The file name is ${path.basename(__filename)}`
);
```
 So another thing that we can do is let's take a look at what's else is available to us as part of that global object. To do so, we're going to use a for loop. So we'll say let key in global and then we'll console.log each one of these keys. So what we're saying here essentially is let's take a look at that global object and specifically, let's look at all of the keys that are part of that object. So you want to hit Save again, you want to run this again. Remember, you can hit the up arrow to see all of the previous commands that you've run. And this is going to give you some information about the global is available is here as well as a bunch of timing functions. So we're going to discuss some of these other global elements in the next couple lessons.
 ```
 for (let key in global) {
  console.log(key);
}

 ```