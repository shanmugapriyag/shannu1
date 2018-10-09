var express = require('express');
var app = express();
var bodyParser=require('body-parser');
var urlencodedParser=bodyParser({extended:false})
var fs= require('fs');

app.use(express.urlencoded());
app.get('/', function (req, res) {
    res.sendFile(__dirname+'/'+ "icecream.html");

app.post('/',function(req,res){
            
var t1=Number(req.body.price);
    var t2= Number(req.body.quantity);
    
     var total= t1*t2;

     var details={
        name: req.body.name,
        Icecream:req.body.select,
        Quantity:req.body.quantity,
        Price:req.body.price,
        Total: total

    };
    fs.appendFile('receipt.text',JSON.stringify(details),(err,result)=>{

        if(err) throw err;
        else{
            console.log("appended succesfully");
        }
    });
    res.end(`${total}`);
})
}); app.listen(3000);

   console.log("connected");
   -------------
   <!DOCTYPE html>
<html>
    <head>
        <title>ICE CREAM SHOP</title>
       
        <script>
            var update=function()
           {
           var item = document.getElementById("select");
           var strUser = item.options[item.selectedIndex].text;
       
                        
        if(strUser=='Vanilla'){
        
     document.getElementById("price").value = "70";

        }
        else if(strUser=='Chocolate'){
            alert(item);
            document.getElementById('price').value="100";
        }
        else if(strUser=='Butter Scotch'){
            document.getElementById("price").value = "80";
        }
        else if(strUser=='Black Current'){
            document.getElementById('price').value="50";
        }
        else{
            document.getElementById('price').value="0";
            
        }
}
        function cancel (){

            return;
            }
        </script>
    </head>


    <body>
        <h1 align=center>ICE CREAM SHOP</h1>
        <form action="http://localhost:3000/" method="POST">
        <table>

            <tr>
                <td>Name:</td>
                <td><input type=text name="name"></td>
            </tr>
            <tr>
                    <td>Flavours:</td>
                    <td><select name="select" id="select" onchange="update();">
                            <option value="empty" name="empty">Select</option>
                            <option value="vanilla" name="Vanilla">Vanilla</option>
                            <option value="chocolate" name="chocolate">Chocolate</option>
                            <option value="butterscotch" name="butterscotch">Butter Scotch</option>
                            <option value="blakcurrent" name="blackcurrent" >Black Current</option>
                          </select>
                          
                    </td>
            </tr>

                  <tr>
                    <td>Price:</td>
                    <td><input type=text name="price" id="price" > </td>
                </tr>
                    <tr>
                        <td>Quantity:</td>
                        <td><input type=text name="quantity"></td>
                    </tr>

                       <tr>
                            <td>Buy:</td>
                            <td><button>Buy</button></td>
                        </tr>
                        <tr>
                                <td>Cancel:</td>
                                <td><input type=submit  value="Cancel">
                                </td>
                            </tr>

        </table>
            

        </form>

    </body>

</html>
--
var express=require ('express');
var app=express();
var bodyParser=require('body-parser');
var urlencodedParser=bodyParser({extended:false})
app.use(express.urlencoded());

app.get('/',function(req,res){
    var details={
        "user1" : {
      "name" : "mahesh",
	  "password" : "password1",
	  "profession" : "teacher",
	  "id": 1
   }  

  };   res.json(details);

});app.listen(3000);
