## I. Async Programming:

+ Async programming is common in JS 
+ The classic solution is **callback**
+ **Main problem is one callback per async task**
+ **Another problem is nested callback**
+ Another try is Listeners
+ **Problem is that there is no reaction when an async function ends before the listener registers. Hard to debug**

## II. Promises

+ Object keeps result of async function *pending, resolved, rejected*
+ Represents the eventual completion (or failure) of an asynchronous operation and its resulting value
+ **then()**: returns a Promise. it takes up to two arguments: **success and failure**
+ **reject()**: returns a promise that is rejected with given reason
+ **resolve()**: returns a promise that is resolved with given value
    + If the value is a promise, that promise is returned
    + If the value is a thenable, the returned promise will "follow" that thenable adopting its eventual state
    + **Call Promise.resolve on thenable that resolves itself will create an infinite loop**
    
+ **catch()**: returns promise and deals with err
+ **finally()**: returns Promise and when the promise is settled, the specific callback function is executed

+ **Promise.all()**: resolves an iterable of promise

## III. Async/Await:

+ Cannot be used with plain callbacks or node callbacks
+ It is non-blocking
+ Makes Async code looks and behave likes synchronous code
+ Async function returns a promise implicitly and the resolve value of the promise will be whatever you return from the function
+ **Benefits**:
    + *Error Handling*: Could be done by try/catch
    + *Cleaner Code*
    + *Intermediate value*: the value of a promise is the argument of the next one
    + *Debugging*: 

## IV. Node Core Concepts:

1. **Global Scope && Objects**:
    + Browser by default put everything in global scope
    + Node.js was designed to behave differently with everything being local by default
    + Global modules
        *__filename* : file of the code
        *__dirname*: the name of the directory
        *setTimeout* :  
        *clearTimeout*:
        *setInterval()*
        *Console*:
        *Process*

2. **Process Object**:
    + *process.pid*: 
    + *process.stdout*:
    + *process.stdin*:
    + *process.stderr*:
    + *process.argv*
    + *process.cwd()*:
    + *process.kill(pid, [signal])*:
    + *process.memoryusage()*
    + *process.chdir()*
    + *process.uptime()*:
    + *process.nextTick()*: allows callback to be scheduled for the next Event Loop Iteration
    
3. **Process Events**:
    + *exit*: when process is about to exit
    + *beforeExit*: when node empties event loop and nothing else scheduled
    + *uncaughtException*: when exception bubbles
    + *Signal Events* : SIGINT or SIGHUP (Hang up)

4. **Module Export and Import**:
    + *exports.name = object*: exports is an object
    + *module.exports = ...*: This exports will overwrite everything
    
5. **Buffer**:
    + Node.js addition to four primitives (bool, string, number and RegExp)
    + Efficient data stores
    + Used when reading from file, receiving packets 
    
6. **File system**:
    + *fs module*: provide ways to read and write, can be async or sync.
    
7. **Data streams**:
    + Processing data while still receiving it
    + Useful for large datasets, like video or data migration
    + *fs.readFile* will put the whole file content in memory before writing out in response
    + *fs.createReadStream* will read one chunk at a time
    
8. **Event Loop**:
    + Event loop is running on the same thread 
    + Event loop process tasks based on round-robin
    + Each iteration of event loop is called a **tick**
    