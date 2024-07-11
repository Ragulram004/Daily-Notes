## Two issues while using callbacks
1. **Callback Hell** 
	#callbackhell #callback #asynchronous
	- When a function is passed as an argument to another function, it becomes a callback function. 
	- This process continues and there are many callbacks inside another's Callback function. This grows the code horizontally instead of vertically. That mechanism is known as callback hell.
			**The errors that can occur in callback hell are:**
				- **Uncaught Exception**: This error occurs when an exception is thrown but not caught by any try-catch block. It can cause the program to crash.
				- **Infinite Loop**: This error occurs when a callback function is called repeatedly without any exit condition. It can cause the program to hang.
				- **Callback Not Invoked**: This error occurs when a callback function is not invoked at all. It can cause the program to halt.
				- **Callback Invoked Multiple Times**: This error occurs when a callback function is invoked multiple times. It can cause the program to behave unexpectedly.
			
2. **Inversion of Control** #inversionofcontrol #asynchronous
	- The callback function is passed to another callback, this way we lose the control of our code. We don't know what is happening behind the scene and the program becomes very difficult to maintain. That process is called inversion of control.
```js
	//reference code - do not provide output.
	const cart - ["shoes","pants","kurta"];
	api.createOrder(cart, function (){
		api.proceedToPayment(function (){
			api.showOrderSummary(function (){
				api.updateWallet();
			})
		})
	})
```
- The above structure is known for callback hell. #callbackhell 
- The entire api function is blindly under the control of the api.createOrder function. This makes difficulties while runtime this is known as inversion of control.  #inversionofcontrol 
- This can be solved by [[15. Promise]].