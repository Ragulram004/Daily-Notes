#map #jsmap
```js
const users = [
	{firstName:"Ragul", lastName:"Balasaravanan", age: 18},
	{firstName:"Ram", lastName:"Balasaravanan", age: 18},
	{firstName:"Radha", lastName:"Balasaravanan", age: 41},
	{firstName:"Elon", lastName:"Musk", age: 52},
];

//List of full names for all the users
const output = users.map((x) => x.firstName + " " + x.lastName);
console.log(output);
```
	![[Pasted image 20240126172921.png]]
----------
#reduce #jsreduce
```js
const users = [
	{firstName:"Ragul", lastName:"Balasaravanan", age: 18},
	{firstName:"Ram", lastName:"Balasaravanan", age: 18},
	{firstName:"Radha", lastName:"Balasaravanan", age: 41},
	{firstName:"Elon", lastName:"Musk", age: 52},
];

//{18:2, 41:1 , 51:1}

const output = users.reduce(function(acc,curr){
	if(acc[curr.age]){ //acc is like a storage this condition check for curr age in the acc.
		acc[curr.age]++
	}else{
		acc[curr.age] = 1;
	}
	return acc
},{})
console.log(output);
```

	![[Pasted image 20240126174225.png]]
--------------
#filter #jsfilter 
```js
const users = [
	{firstName:"Ragul", lastName:"Balasaravanan", age: 18},
	{firstName:"Ram", lastName:"Balasaravanan", age: 18},
	{firstName:"Radha", lastName:"Balasaravanan", age: 41},
	{firstName:"Elon", lastName:"Musk", age: 52},
];
//firstName of age less that 30

const output = users.filter((x)=> x.age<30).map((x)=>x.firstName);
console.log(output);
```

	![[Pasted image 20240126175033.png]]
---------
The above concept using the reduce();
```js
const users = [
	{firstName:"Ragul", lastName:"Balasaravanan", age: 18},
	{firstName:"Ram", lastName:"Balasaravanan", age: 18},
	{firstName:"Radha", lastName:"Balasaravanan", age: 41},
	{firstName:"Elon", lastName:"Musk", age: 52},
];
//firstName of age less that 30

const output = users.reduce(function(acc,curr){
	if(curr.age<30){
		acc.push(curr.firstName);
	}
	return acc;
},{})
```