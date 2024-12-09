# Node.js Server Hangs on Long-Running Operations

This repository demonstrates a common issue in Node.js servers: hanging due to long-running operations in synchronous code.  The example shows a server that hangs for 5 seconds before responding, blocking any other requests during that time. This is problematic for responsiveness and scalability.

The `bug.js` file contains the problematic code, while `bugSolution.js` provides a corrected implementation that utilizes asynchronous operations to avoid blocking.

## How to Reproduce

1. Clone the repository.
2. Navigate to the project directory: `cd node-server-hang`
3. Run the buggy server: `node bug.js`
4. Make multiple requests to `http://localhost:3000` using tools such as curl or a browser. Observe that responses are delayed because of the long running operation. 
5. Stop the server using `Ctrl+C`. 
6. Now, run the fixed version: `node bugSolution.js`
7. Repeat step 4. Note the improved responsiveness. 

## Solution

The solution involves using asynchronous operations to prevent blocking the main event loop.  This allows Node.js to handle multiple requests concurrently without delays. 