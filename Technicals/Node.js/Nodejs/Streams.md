![[Pasted image 20240812153846.png]]
```node
const fs = require('fs')


const readable = fs.createReactStream("Source_file")
readable.on("data" ,chunk =>{
	res.write(chunk);
})
readable.on("end" , () =>{
	res.end()
})
readable.on("error" , err =>{
	console.log(err)
	res.statusCode = 500
	res.end("File not Found")
})
```
#### Using pipe() makes still more efficient
```node
const readable = fs.createReadStream("Source_file")
//readableSource.pipe(WritableDestination)
readable.pipe(res);
```