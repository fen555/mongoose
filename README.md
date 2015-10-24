# mongoose
####1.พิมพ์
```sh
npm init
npm install express --save
```
####2.สร้างไฟล์ชื่อ server.js ละพิมพ์โค้ด
```sh
var express = require('express')

var app = express()

app.get('/', function(req,res){
	res.send("Hello")
})

app.listen(3000)
console.log('run in 3000')
```
####3.ลองทดสอบโปรแกรมด้วย
```sh
node server.js
```
####4.ลง body-parser
```sh
npm install body-parser --save
```
####5.เปลี่ยนโค้ดทั้งหมดใน server.js เป็นดังนี้
```sh
var express = require('express')
var bodyParser = require('body-parser')

var app = express()

app.use(bodyParser.urlencoded({extended : true}))
app.use(bodyParser.json())

app.get('/', function(req,res){
	res.send("Hello")
})

app.listen(3000)
console.log('run in 3000')
```
####6.ลง mongoose
```sh
npm install mongoose --save
```
####7.เรียกใช้ mongoose และใช้เพิ่มคำสั่งเชื่อมต่อ โดยเปลี่ยนโค้ดทั้งหมดเป็นดังนี้
```sh
var express = require('express')
var bodyParser = require('body-parser')
var mongoose = require('mongoose')

mongoose.connect('mongodb://localhost/db')

var app = express()

app.use(bodyParser.urlencoded({extended : true}))
app.use(bodyParser.json())

app.get('/', function(req,res){
	res.send("Hello")
})

app.listen(3000)
console.log('run in 3000')
```
####8. สร้างโฟลเดอร์ขึ้นมาใหม่ ระดับเดียวกับไฟล์ server.js ชื่อ routes และ models
####9. สร้างไฟล์ใน routes ชื่อ api.js
####10. สร้างไฟล์ใน models ชื่อ grade.js
####11. ลง
```sh
npm install node-restful --save
```
####12. เพิ่มโค้ดใน grade.js
```sh
var restful = require('node-restful')
var mongoose = restful.mongoose

var grade = new mongoose.Schema({

	name : String,
	grade : String

})

module.exports = restful.model('grade',grade)
```
####13. ใน api.js
```sh
var express = require('express')
var router = express.Router()

var Grade = require('../models/grade')

Grade.methods(['get','put','post','delete'])
Grade.register(router, '/grade')

module.exports = router
```
####14. ใน server.js ให้เปลี่ยนโค้ดเป็น
```sh
var express = require('express')
var bodyParser = require('body-parser')
var mongoose = require('mongoose')

mongoose.connect('mongodb://localhost/db')

var app = express()

app.use(bodyParser.urlencoded({extended : true}))
app.use(bodyParser.json())

app.use('/api',require('./routes/api'))

app.listen(3000)
console.log('run in 3000')
```
####15. 
