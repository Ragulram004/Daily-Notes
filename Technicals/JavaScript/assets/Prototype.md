#prototype #objects #hiddenprototype
- When ever you create a variable or objects or functions it is provided with **default hidden properties and methods**.
```js
let arr = ["Ragul","Ram"];
let object = {
	name:"Ragul"
	city:"Salem"
	getIntro: function (){
		console.log(this.name+"from"+this.city);
	}
}
function func(){

}
```
- When ever we create an object JS engine will put this hidden properties and methods inside an object and attach the this object to the object we created.
- The methods are can be seen by
```js
arr.__proto__.------- //hifens are the properties visible
```
	![[Pasted image 20240123232145.png | 500]]
- It is same objects for **Array.prototype**. The prototype for Array.
	![[Pasted image 20240123232254.png | 500]]
- At the same time the array prototype has prototype for itself.
```js
arr.__proto__.__proto__ // prototype for arr.proto
```
- There is prototype for objects and functions also.
```js
arr.__proto__.__proto__  == fun.__proto__.__proto__ ==  object.__proto__
```
-----
#prototypechain 
```js
arr.__proto__.__proto__.__proto__ // It is actually null. That is end of the prototype chain.
```
	![[Pasted image 20240123233354.png | 500]]
	![[Pasted image 20240123234018.png | 500]]
-----
```js
let object = {
	name:"Ragul",
	city:"Salem",
	getIntro: function (){
		console.log(this.name+"from"+this.city);
	}
}
let object2 = {
	name : "Ram"
}

object2.__proto__ = object; //never do this
//------------------------------------------------------------
//proto comparison output at console.
object.__proto__ == object2.__proto__
//console
object2.name //Ram
object2.city //Salem from object --> This is posible because object2 proto is assigned as object. The engine will check for the city in object2, if it is not present then it will move to it's proto this how city in printed.
```
	![[Pasted image 20240124112335.png]]
```js
object.getIntro 
onject2.getIntro
// Checks for availablity at this not if not it will go to in proto.
```
	![[Pasted image 20240124113007.png | 300]]
-----
```js
Function.prototype.mybind = function(){
	console.log("Created Proto mybind")
}

function func(){
}
function func2(){
}
```
Output:
	![[Pasted image 20240125143857.png | 300]]
	