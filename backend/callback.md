## Callback
A callback is basically where a function accepts another function as a parameter. 
At some point during execution the called function will execute the function passed as a parameter, this is a callback

Examples:
- Callback functions can be used for updates, sort of like hooking into another function. For example, consider a 
function that downloads files using http. Your application may want to display progress to the user. You could pass a 
callback function (display progress) into the download function so that it calls your display function everytime 
it reads from the socket


## Reference
1. https://en.wikipedia.org/wiki/Callback_(computer_programming)
2. https://pytorch-lightning.readthedocs.io/en/latest/extensions/callbacks.html
