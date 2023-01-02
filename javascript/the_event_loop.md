The main thread: where all of the javascript code is ran
There are ways you can run code away from the main thread:
setTimeout: come back and run this code later, and creates a separate thread waits the appropriate time for the setTimeout then it tells the main thread to execute the code within the setTimeout
If we did the waiting on the main thread then everything else in the program would have to wait as well
Promise waits to resolve until the currently running function is complete, as soon as a promise resolves then it’ll run, the event loop wants to run promises quicker, but setTimeout has to wait
https://www.youtube.com/watch?v=cCOL7MC4Pl0 