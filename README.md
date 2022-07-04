<!DOCTYPE html>
<html>
	<head>	
	</head>
	<body>
		<h2>Event Management</h2>
		<label for="name">Event Name</label>
		<input type="text" name="name" id="name"/>
		<br />
		<label for="venue">Venue</label>
		<input type="text" name="venue" id="venue"/>
		<br />
		<label for="date">Date</label>
		<input type="date" name="date" id="date"/>
		<br />
		<label for="price">Cost/day</label>
		<input type="text" name="price" id="price"/>
		<br />
		<label for="count">No of days Needed</label>
		<input type="text" name="count" id="count"/>
		<br />
		<input id="addEvent" type="button" onclick="addEvent()" value "Add Event"/>
		<div id="result"></div>
		<script src="./script.js"></script>
	</body>
</html>





var event_arr=[];

function addEvent(){

	var event1={

		name: document.getElementById("name").value,
		venue: document.getElementById("venue").value,
		date: document.getElementById("date").value,
		price: document.getElementById("price").value,
		days: document.getElementById("count").value

	};
	event_arr.push(event1);
	display();
	
}
function display(){
	tableStart =`<table id='resultTable'>
      <tr>
	<td>Event Name</td>
	<td>Venue</td>
	<td>Date</td>
	<td>Total Cost</td>
	<td>Cancel Event</td>
	</tr>`;
	
	tableEnd = `</table>`;
	tableRows= ``;
	event_arr.forEach((event1, index) => {
		event1.id='link'+index;
		tableRows += `<tr>
						<td>${event1.name}</td>
						<td>${event1.venue}</td>
						<td>${event1.date}</td>
						<td>${event1.price*event1.days}</td>
						<td><a href="#" id="${event1.id}" onclick="deleteElement(this.id)">Cancel</a></td>
					</tr>`;
					
	});

	var table = tableStart+tableRows+tableEnd;
	document.getElementById("result").innerHTML= table;
		
}

function deleteElement(id){

	if(event_arr.length == 1){
		document.getElementById("result").innerHTML= "No Events available";
	}else{
	event_arr = event_arr.filter(event1 => event1.id != id);
	display();
	}



}
