//  -----------------------------      Header File Information      ------
-------------------------//
// Document Name:    project5.js
// Author Name:      Eric Moore
// Date Created:     4/20/21
// Date Updated:     5/2/21	
// Descriptions:     nodejs file that reads an html file and prints it out on a server
created by the nodejs. The nodejs also processes the pic.png in the html file as well
lastly the file reads the information of the .json file. It prints out the predictions
made by the json file into the CMD.	
//
// -----------------------------------------------------------------------
---------------------------------- //

var http = require('http');
var fs = require('fs');
var path = require('path');

let filename = fs.readFileSync("project5.json");
let temp = JSON.parse(filename);

http.createServer(function(req, res){
     
	if(req.url.includes("pic.png")){
		fs.readFile('pic.png', function (err, data){
			res.writeHead(200, {"Content-Type": 'image/png'});
			res.write(data);
			res.end();

		});
	}
	else{
		fs.readFile('project1.html', function (err, data){
			res.writeHead(200, {"Content-Type": 'text/html'});
			res.write(data);
			res.end();

		});
	}
}).listen(8000);

console.log('Server running at http://127.0.0.1:8000/');

console.log("-------------- Your Predictions --------")
console.log("Networking: " + temp.Facebook.Networking);
console.log("Networking: " + temp.Facebook.MarketList);
console.log("Networking: " + temp.Facebook.MarketCap);
console.log("--------------------------------------------");
console.log("Networking: " + temp.Twitter.Networking);
console.log("Networking: " + temp.Twitter.MarketList);
console.log("Networking: " + temp.Twitter.MarketCap);
console.log("--------------------------------------------");
console.log("Networking: " + temp.Instagram.Networking);
console.log("Networking: " + temp.Instagram.MarketList);
console.log("Networking: " + temp.Instagram.MarketCap);
console.log("--------------------------------------------");
console.log("Networking: " + temp.YouTube.Networking);
console.log("Networking: " + temp.YouTube.MarketList);
console.log("Networking: " + temp.YouTube.MarketCap);
console.log("--------------------------------------------");