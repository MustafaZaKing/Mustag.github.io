<!DOCTYPE html>
<html lang="en">

<head>
<meta charset="UTF-8">
<title>AutoBid Car Marketplace</title>

<style>

body{
font-family: Arial;
margin:0;
background:#f4f4f4;
}

header{
background:#111;
color:white;
text-align:center;
padding:20px;
}

.search-box{
text-align:center;
margin:20px;
}

.search-box input{
padding:10px;
width:300px;
font-size:16px;
}

#carContainer{
display:grid;
grid-template-columns:repeat(auto-fill,minmax(250px,1fr));
gap:20px;
padding:20px;
}

.carCard{
background:white;
padding:15px;
border-radius:10px;
box-shadow:0 4px 10px rgba(0,0,0,0.1);
}

button{
margin:5px 3px;
padding:8px 10px;
border:none;
border-radius:5px;
cursor:pointer;
background:#222;
color:white;
}

button:hover{
background:#444;
}

</style>

</head>

<body>

<header>
<h1>🚗 AutoBid Car Marketplace</h1>
<p>Buy • Bid • Book • Service Cars</p>
</header>


<div class="search-box">
<input id="searchInput" placeholder="Search cars..." onkeyup="searchCars()">
</div>


<div id="carContainer"></div>


<script>

let cars = [

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
year:2015 + (i % 10),
price:15000 + (i*200)
})
}


function displayCars(list){

let container = document.getElementById("carContainer")

container.innerHTML=""

list.forEach((car,index)=>{

let card = document.createElement("div")

card.className="carCard"

card.innerHTML = `
<h3>${car.model}</h3>
<p><b>Year:</b> ${car.year}</p>
<p><b>Price:</b> $${car.price}</p>

<button onclick="carInfo(${index})">Info</button>
<button onclick="bidCar(${index})">Bid</button>
<button onclick="bookCar(${index})">Book</button>
<button onclick="serviceCar(${index})">Service</button>
`

container.appendChild(card)

})

}


function carInfo(id){

let car=cars[id]

alert(
"Car Information\n\n"+
"Model: "+car.model+
"\nYear: "+car.year+
"\nPrice: $"+car.price
)

}


function bidCar(id){

let bid = prompt("Enter your bid price")

if(bid){
alert("Bid submitted: $"+bid)
}

}


function bookCar(id){

let name = prompt("Enter your name")

let date = prompt("Booking date")

if(name && date){
alert("Booking confirmed for "+name+" on "+date)
}

}


function serviceCar(id){

let service = prompt("Enter service (repair / cleaning / inspection)")

if(service){
alert("Service request sent: "+service)
}

}


function searchCars(){

let value=document.getElementById("searchInput").value.toLowerCase()

let filtered=cars.filter(car =>
car.model.toLowerCase().includes(value)
)

displayCars(filtered)

}


displayCars(cars)

</script>

</body>
</html>
