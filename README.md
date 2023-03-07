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

 #### 2.3 Handling argument variables with process.argv
 ```
 console.log(process.argv)
 ```
One important object that's available to us globally is the process object. So it can be accessed from absolutely anywhere, and it contains functionality that allows us to interact with information about the current process instance. With the process object, we can get environment information, read environment variables, communicate with the terminal, and we can exit the current process. So it gives us a way to work with that current process instance. So one of the things that we can do with the process object is collect information from the terminal. So this information is stored in the process.argv array. So check this out. We're going to get rid of the code that was here before and replace it with a console log to figure out what is available in this process.argv value. Now, we want to make sure that we're navigated to the right file here, and we can run node global. This will then return to us this process.argv array. As you can see, it's an array that contains the path to node as well as the path to the file. So basically what we're seeing here is everything that I have sent when I created this command. So the location of node where that's running and then the file itself. 
```
node global --user Uzzal --greting "Hello from node"
```
Let's try to run our app again, but this time we're going to pass in some more information. So we'll say --user and then our name, and then we'll say --greeting, and we'll say "hello from node." Now if we hit Enter, we see a larger array. Now the process argv array starts with the same two things at the beginning, but each additional array value represents the rest of what we typed into the console after the global module. So we see our user flag and our name, and we see our greeting flag and the greeting. So let's try to create the little function that's going to help us process some of these values. We're going to create a function called grab, and here we're going to grab this flag. We will say let indexAfterFlag equal process.argv.index of flag, plus one. So this is going to give us the position of the index after the flag. So whatever this value is and whatever this value is. So we're going to grab it this way. We'll say return process argv and then the index we want to grab is the index after the flag. So now let's try to grab the value after the greeting. We'll say let greeting equal grab --greeting, and then we'll say let user equal grab. We'll call that grab function, and this time we want to pass it the user flag. Perfect, so now we can console-log the greeting, and then we'll console-log the user. I also want to stop console-logging the process argv value up here. We'll just delete that, just so we don't get confused, and then check it out. We have been able to isolate the value that we've passed in with that flag for both. So utilizing this process.argv array is going to let us collect user input. We can create all sorts of cool command line applications with node just by understanding this array.
```
function grab(flag) {
    let indexAfterFlag = process.argv.indexOf(flag) + 1;
    return process.argv[indexAfterFlag];
}

let greeting = grab("--greeting");
let user = grab("--user")

console.log(greeting)
console.log(user)
```
Run
```
node global --user Uzzal --greting "Hello from node"
```

#### 2.4 Working with standard input
Another feature of the process object is standard input and standard output. These two objects offer us a way to communicate with a process while it's running. So what we're going to do next is we want to make sure that we're in our global file and that we're navigated to the right spot in the terminal, get rid of the code that's here, and replace this with process.stdout.write, and here, we're just going to add Hello, a couple of spaces, and let's try to run this. So node global, and then we'll see Hello, and then when we use stdout.write, we're sending some strings to the terminal. So here what we could do is add some new lines with the \n, and then this is going to add those lines for us. What we want to do next is we want to create an array of questions. So here we'll say const questions, and we'll add a few strings here. So we'll say, What is your name?, What would you rather be doing?, and then we'll say, What is your preferred programming language. Excellent. So we have our questions, then we're going to create an empty array of answers. So here is our answers array. And then finally, we're going to create a function called ask. So ask is going to take i in as an argument. So i is going to stand in for the index for one of these questions. And here we go. We're going to say process.stdout.write. We'll add a couple new lines here, /n/n. We actually don't need the space in between those. And then, let's go ahead and say questions i, perfect. And because we're using this template string, holy moly, I need to make sure that I'm making this a template string with back ticks. And then finally, let's go ahead and add a little prompt for ourselves, we're going to say process.stdout.write, and then we'll add this little caret to indicate to ourselves that we are trying to accept some sort of input. Then finally, we're going to invoke the question. So we'll say, ask answers.length. And now let's try to run this again. Cool. So notice that running the app is going to ask the first question. It prompts the user for an answer, and then it quits. So we also leave the terminal out of whack because we use standard output here. So what we actually want to do is wait until the user answers the question. So what we can do is listen for a data event on this object using a function. So we're going to say process.stdin.on data, then we'll pass in a function here with the argument data, and here we'll say process.stdout.write data.toString.trim. So now we can continue to call ask with answers.length, and let's check this out. It says, What is your name? Eve. I'll say, that's my name, and it copies me. Stop it, stop it. (laughs) It's always copying me. By adding the listener, we start using node asynchronously. So every other app we've run until now has run through the command synchronously and quit, leaving us back at the terminal prompt. But this time the app is still running. It's waiting for some input. So in the next lesson, I'm going to talk to you about how we can stop the process when we're out of data and we're out of these prompts.
```
process.stdout.write("Hello ");
```
node global.js

```
process.stdout.write("Hello \n\n"");
```

node global.js

```
process.stdout.write("Hello \n\n"");

const questions = [
    "What is your name?",
    "What would you rather be doing?",
    "What is your preferred programming language"
];

const answers = [];

function ask(i) {
    process.stdout.write(`\n\n\n${questions[i]}`);
    process.stdout.write(` > `);
}

process.stdin.on("data", function(data) {
    process.stdout.write(data.toString().trim());
});

ask(answers.length);
```
#### 2.5 Using standard output
So with our file, we want to change the code a bit to collect answers from our terminal. So the first thing we want to do is let's make sure to move our ask function above our process standard input. Another thing I'm noticing here is that this is looking for answers.length. If we wanted to set this to be an empty array, we could always add a default here. So we could add a default argument to this function and remove this from our function invocation here. So that's one thing we can do. The second thing I want to do is instead of echoing the answer back out, let's go ahead and add this to the array. So we're going to replace process standard input.write with answers.push. We'll take data, convert it to a string and trim off any white space. The next thing we want to do is say if our answers.length is less than our questions.length, then we want to call the ask function again with answers.length. So whatever the length of that answers array is. Otherwise, if there are as many answers as there are questions, we want to call process.exit to tell our process to quit. Now if we run node global again, it'll say what is your name? What would you rather be doing? What is your preferred programming language? And there we go. Now we can answer our questions and as we cycle through them, we're saving our answers but we've collected them but we're not really doing anything with them yet. So let's go back and display the results. In addition to this data event where if we have some new data, we're going to do everything that's inside of this function. We're going to call process.on and whenever we call exit, we're going to call another function. So check this out. First, we're going to say process.standard output. So write this to the terminal. We'll add some spaces here. Then we'll say process standard output.write and we're going to use a template string to add the message. We'll say Go answers one. We'll add a space. Answers zero and then you can say you can finish writing answers two later. Okay, so that's a long, long string but check this out. This is going to pluck the second item from the array, the first item from the array, our name, and then the programming language of choice to add that to our string. So let's see what we get. We're going to take another look. Node global, what's your name? What would you rather be doing? What's your preferred programming language. Go Skiing Eve you can finish writing JavaScript later. So our program is extremely friendly. It's some good advice. I'm going to trust the technology and end the lesson here. But before I do, remember the standard input and standard output objects give us some powerful tools for communication with running a process. So these tools are available on the process object, meaning that you can use them anywhere.