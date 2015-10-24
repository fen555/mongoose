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
