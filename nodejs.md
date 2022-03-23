# nodejs

## debug node.js

`debugger;` in your code.  
`node inspect script.js` in the cl.

## reclaim node web server port

Didn't safely quit using `ctrl+c`?

Get the process id  
`lsof -t -i:8080` then `kill -9 <pid>`  
One-liner: `kill -9 $(lsof -t -i:8080)`  
Or kill node's process  
`pkill -f node`
