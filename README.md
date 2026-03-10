<!DOCTYPE html>
<html>

<head>

<title>AutoBid Car Marketplace</title>

<style>

body{
font-family:Arial;
margin:0;
background:#f2f2f2;
}

header{
background:black;
color:white;
padding:20px;
text-align:center;
}

.search{
text-align:center;
padding:20px;
}

input{
padding:10px;
width:250px;
}

#cars{
display:grid;
grid-template-columns:repeat(4,1fr);
gap:20px;
padding:20px;
}

.car{
background:white;
padding:15px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.2);
}

button{
padding:8px;
margin:5px;
cursor:pointer;
}

</style>

</head>


<body>

<header>

<h1>🚗 AutoBid Marketplace</h1>
<p>Buy • Sell • Bid • Book Cars</p>

</header>


<div class="search">

<input type="text" id="search" placeholder="Search cars..." onkeyup="searchCars()">

</div>


<div id="cars"></div>


<script>


let cars=[

{model:"Toyota Camry",year:2022,price:27000},
{model:"Honda Accord",year:2021,price:26000},
{model:"Toyota Corolla",year:2023,price:22000},
{model:"Honda Civic",year:2022,price:24000},
{model:"Ford Mustang",year:2021,price:42000},
{model:"BMW 3 Series",year:2020,price:41000},
{model:"Mercedes C Class",year:2021,price:43000},
{model:"Audi A4",year:2022,price:42000},
{model:"Tesla Model 3",year:2023,price:47000},
{model:"Tesla Model S",year:2022,price:90000}

];


for(let i=0;i<110;i++){

cars.push({
model:"Car Model "+(i+1),
year:2014+(i%10),
price:15000+(i*300)
})

}



function showCars(list){

let container=document.getElementById("cars")

container.innerHTML=""

list.forEach((car,index)=>{

container.innerHTML+=`

<div class="car">

<h3>${car.model}</h3>

<p><b>Year:</b> ${car.year}</p>

<p><b>Price:</b> $${car.price}</p>

<button onclick="info(${index})">Info</button>

<button onclick="bid(${index})">Bid</button>

<button onclick="book(${index})">Book</button>

<button onclick="service(${index})">Service</button>

</div>

`

})

}



function info(id){

let car=cars[id]

alert(
"Car Info\n\n"+
"Model: "+car.model+
"\nYear: "+car.year+
"\nPrice: $"+car.price
)

}



function bid(id){

let car=cars[id]

let bidPrice=prompt("Enter your bid price for "+car.model)

if(bidPrice){

alert("Your bid of $"+bidPrice+" was submitted!")

}

}



function book(id){

let name=prompt("Enter your name")

let date=prompt("Enter booking date")

if(name && date){

alert("Booking confirmed for "+name+" on "+date)

}

}



function service(id){

let serviceType=prompt("Enter service needed (inspection / cleaning / repair)")

if(serviceType){

alert("Service request submitted for "+serviceType)

}

}



function searchCars(){

let value=document.getElementById("search").value.toLowerCase()

let filtered=cars.filter(car=>

car.model.toLowerCase().includes(value)

)

showCars(filtered)

}



showCars(cars)


</script>


</body>

</html>
