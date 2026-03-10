# Attendance-calculator
Attendance calculator for students
<!DOCTYPE html>
<html lang="en">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Attendance Percentage Calculator</title>

<style>

body{
font-family: Arial;
background: linear-gradient(135deg,#4facfe,#00f2fe);
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

.container{
background:white;
padding:30px;
border-radius:12px;
width:350px;
text-align:center;
box-shadow:0 6px 15px rgba(0,0,0,0.2);
}

h2{
margin-bottom:20px;
}

input{
width:90%;
padding:10px;
margin:10px 0;
border-radius:6px;
border:1px solid #ccc;
font-size:16px;
}

button{
padding:10px 20px;
background:#007BFF;
color:white;
border:none;
border-radius:6px;
cursor:pointer;
font-size:16px;
}

button:hover{
background:#0056b3;
}

.result{
margin-top:15px;
font-size:18px;
font-weight:bold;
}

.warning{
color:red;
}

.success{
color:green;
}

.info{
margin-top:10px;
font-size:14px;
}

</style>

</head>

<body>

<div class="container">

<h2>Attendance Calculator</h2>

<input type="number" id="totalClasses" placeholder="Enter Total Classes">

<input type="number" id="attendedClasses" placeholder="Enter Attended Classes">

<br>

<button onclick="calculateAttendance()">Calculate</button>

<div class="result" id="result"></div>

<div class="info" id="extraInfo"></div>

</div>

<script>

function calculateAttendance(){

let total = document.getElementById("totalClasses").value;
let attended = document.getElementById("attendedClasses").value;

if(total=="" || attended==""){
document.getElementById("result").innerHTML="Please enter all values";
return;
}

total = parseInt(total);
attended = parseInt(attended);

if(attended > total){
document.getElementById("result").innerHTML="Attended classes cannot be greater than total classes";
return;
}

let percentage = (attended/total)*100;
percentage = percentage.toFixed(2);

let resultBox = document.getElementById("result");
let infoBox = document.getElementById("extraInfo");

resultBox.innerHTML="Attendance: "+percentage+"%";

if(percentage < 75){

resultBox.className="result warning";

let needed = Math.ceil((0.75*total)-attended);

infoBox.innerHTML="⚠ Your attendance is below 75%.<br>You need to attend next <b>"+needed+"</b> classes to reach 75%.";

}

else{

resultBox.className="result success";

infoBox.innerHTML="✅ Good! You are eligible for exams.";

}

}

</script>

</body>

</html>
