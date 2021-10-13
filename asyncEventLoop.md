# Promises, Async & the Event Loop

## Intro

JavaScript is single threaded and has a synchronous execution model. Single threaded means that one command is being executed at a time.
However, with the introduction of ES6 in 2015 (and then the ES7 in 2017), asynchronous JavaScript allows code to continue being executed while we wait for the result of an initiated action, such as starting a timer, reading a file, or requesting data from a server. While the timer is running, the file is being read, or the server is calculating its response, the thread of execution continues. This is called "non-blocking" behavior, and it results in better performance than what would come from waiting for things to resolve before continuing to the next line of code (which is called "blocking" behavior).



An async function is a function declared with the `async` keyword, and the `await` keyword is permitted within them. The `async` and `await` keywords enable asynchronous, promise-based behavior to be written in a cleaner style, avoiding the need to explicitly configure promise chains.

A Promise is an object representing the eventual completion or failure of an asynchronous operation, which will be resolved with the value returned by the async function, or rejected with an exception thrown from, or uncaught within, the async function.

A task is any JavaScript code which is scheduled to be run by the standard mechanisms such as initially starting to run a program, an event callback being run, or an interval or timeout being fired. These all get scheduled on the **task queue**.

A microtask is a short function which is executed after the function or program which created it exits and only if the JavaScript execution stack is empty, but before returning control to the event loop being used by the user agent to drive the script's execution environment. These all get scheduled on the **microtask queue**.

## Resources:

### Documentation
**async function**
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function]

**Promise**
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise]

**microtasks**
[https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API/Microtask_guide]
[https://developer.mozilla.org/en-US/docs/Web/API/queueMicrotask]

### Videos
**Promises, Async & the Event Loop**
[https://youtu.be/fOdcuDigxfw]

## Tools:

### Loupe

Loupe is a little visualisation to help you understand how JavaScript's call stack/event loop/callback queue interact with each other.

The best thing to do to understand how this works is watch this video, then when you are ready, go play!

[https://www.youtube.com/watch?v=8aGhZQkoFbQ]

Instructions

- Write some code in the text editor on the left.
- Hit the save-and-run button and watch it run.
- You can create html elements in the gray box at the bottom left by hitting the edit button.
- Listen for DOM events on them with
$.on("button", "click", function () { console.log("hello") }
- Hit the tool icon at the top left to open a menu with extra settings.
- Need more help? Ping @philip_roberts on twitter.

How does this work?

-Loupe runs entirely in your browser.
- It takes your code.
- Runs it through esprima, a JS parser.
- Instruments it a bunch so that loupe knows where function calls, timeouts, dom events, etc happen.
- Adds a whole bunch of while loops everywhere to slow down the code as it runs.
- This modified code is then turned back into JavaScript and sent to a webworker (in your browser) which runs it.
- As it runs, the instrumentation sends messages to the visualisation about what is going on so it can animate things at the right time.
- It also has some extra magic to make dom events, and timers work properly.

(Built by Philip Roberts from &yet. Code is on github.
