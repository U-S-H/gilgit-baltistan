<html lang="ur" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Prime Solutions GB</title><style>
:root{
--primary:#00d4ff;
--dark:#0f172a;
--card:rgba(255,255,255,.08);
}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:sans-serif;
}

body{
background:linear-gradient(135deg,#020617,#0f172a);
color:#fff;
padding:15px;
min-height:100vh;
}

.glass{
background:var(--card);
backdrop-filter:blur(15px);
border:1px solid rgba(255,255,255,.1);
border-radius:20px;
padding:20px;
margin:15px auto;
max-width:700px;
}

.logo{
text-align:center;
cursor:pointer;
}

.logo h1{
font-size:32px;
color:var(--primary);
}

button{
width:100%;
padding:12px;
border:none;
border-radius:12px;
background:var(--primary);
font-weight:bold;
cursor:pointer;
margin-top:10px;
}

input,select{
width:100%;
padding:12px;
border:none;
border-radius:12px;
margin-top:10px;
}

.profile{
display:none;
text-align:center;
}

.profile img{
width:80px;
height:80px;
border-radius:50%;
margin-bottom:10px;
}
</style><script type="module">

import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";

import {
getAuth,
GoogleAuthProvider,
signInWithPopup,
signOut,
onAuthStateChanged
}
from "https://www.gstatic.com/firebasejs/10.8.0/firebase-auth.js";

import {
getDatabase
}
from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

const firebaseConfig = {

apiKey:"AIzaSyBiti-Ih5nxvRQ8Xt9YImiN1X3RnPoXoTI",
authDomain:"gilgit-79048.firebaseapp.com",
databaseURL:"https://gilgit-79048-default-rtdb.firebaseio.com",
projectId:"gilgit-79048",
storageBucket:"gilgit-79048.firebasestorage.app",
messagingSenderId:"784852692962",
appId:"1:784852692962:web:eab87b313e024ebf7953bb"

};

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getDatabase(app);

window.auth = auth;
window.db = db;

const provider = new GoogleAuthProvider();

window.login = async()=>{

try{

await signInWithPopup(auth,provider);

}catch(err){

alert(err.message);

}

};

window.logout = async()=>{

await signOut(auth);

};

onAuthStateChanged(auth,(user)=>{

if(user){

document.getElementById("loginBox").style.display="none";
document.getElementById("profile").style.display="block";

document.getElementById("userName").innerText=user.displayName;
document.getElementById("userEmail").innerText=user.email;
document.getElementById("userPic").src=user.photoURL;

}else{

document.getElementById("loginBox").style.display="block";
document.getElementById("profile").style.display="none";

}

});

</script></head><body><div class="glass logo">
<h1 onclick="checkAdmin()">🏔 Prime Solutions GB</h1>
<p>گلگت بلتستان ٹورازم سروسز</p>
</div><div class="glass" id="loginBox"><h3>Google Login</h3><button onclick="login()">
Google Sign In
</button></div><div class="glass profile" id="profile"><img id="userPic"><h3 id="userName"></h3><p id="userEmail"></p><button onclick="logout()">
Logout
</button></div>
<script type="module">

import {
ref,
push,
onValue
}
from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

window.saveBooking = async () => {

if(!auth.currentUser){

alert("Pehle Login Karein");
return;

}

const city = document.getElementById("city").value;
const phone = document.getElementById("phone").value.trim();

if(phone === ""){

alert("Phone Number Required");
return;

}

const bookingId =
"PSGB-" +
Math.floor(Math.random()*999999);

const bookingData = {

bookingId,
city,
phone,
status:"Pending",
date:new Date().toLocaleString(),
name:auth.currentUser.displayName,
email:auth.currentUser.email

};

await push(
ref(db,"bookings/"+auth.currentUser.uid),
bookingData
);

alert("Booking Saved\nID: "+bookingId);

loadBookings();

};

window.loadBookings = ()=>{

if(!auth.currentUser) return;

onValue(
ref(db,"bookings/"+auth.currentUser.uid),
(snapshot)=>{

let html="";

snapshot.forEach((child)=>{

const d = child.val();

html += `

<div class="card">

<h4>${d.bookingId}</h4>

<p>📍 ${d.city}</p>

<p>📱 ${d.phone}</p>

<p>📅 ${d.date}</p>

<p>📌 ${d.status}</p>

<button onclick="showReceipt(
'${d.bookingId}',
'${d.city}',
'${d.phone}',
'${d.date}',
'${d.status}'
)">
Receipt
</button>

</div>

`;

});

document.getElementById("history").innerHTML =
html || "<p>No Bookings Found</p>";

});
};

window.showReceipt = (
id,
city,
phone,
date,
status
)=>{

document.getElementById("receiptBox").innerHTML=`

<h2>Prime Solutions GB</h2>

<hr>

<p><b>Booking ID:</b> ${id}</p>

<p><b>City:</b> ${city}</p>

<p><b>Phone:</b> ${phone}</p>

<p><b>Date:</b> ${date}</p>

<p><b>Status:</b> ${status}</p>

<hr>

<p>Thank You For Booking</p>

`;

document.getElementById("receiptModal")
.style.display="block";

};

</script><div class="glass"><h3>Tour Booking</h3><input
id="phone"
placeholder="WhatsApp Number">

<select id="city"><option>Hunza</option>
<option>Skardu</option>
<option>Astore</option>
<option>Fairy Meadows</option>
<option>Khaplu</option></select><button onclick="saveBooking()">
Confirm Booking
</button></div><div class="glass"><h3>Booking History</h3><div id="history"><p>No Bookings Yet</p></div></div><div
id="receiptModal"
style="
display:none;
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,.8);
padding:20px;
z-index:999;
overflow:auto;
"><div class="glass"><div id="receiptBox"></div><button onclick="
document.getElementById('receiptModal')
.style.display='none'
">
Close
</button>

</div></div><!-- AUTO LOAD HISTORY --><script>

setTimeout(()=>{

if(window.loadBookings){

loadBookings();

}

},2000);

</script>
<div id="adminPanel"
style="
display:none;
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
overflow:auto;
background:#020617;
z-index:9999;
padding:20px;
"><div class="glass"><h2>Admin Dashboard</h2><p id="totalBookings">Total: 0</p><div id="adminData"></div><button onclick="
document.getElementById('adminPanel').style.display='none'
">
Close
</button>

</div></div><script type="module">

import {
ref,
onValue,
remove,
update
}
from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

const ADMIN_EMAIL =
"nazimkhan01123@gmail.com";

let taps = 0;

window.checkAdmin = () => {

taps++;

if(taps >= 5){

const pin = prompt("Admin PIN");

if(
pin === "5426" &&
auth.currentUser &&
auth.currentUser.email === ADMIN_EMAIL
){

document.getElementById("adminPanel")
.style.display = "block";

loadAdminBookings();

}
else{

alert("Unauthorized");

}

taps = 0;

}

};

window.changeStatus = async (
uid,
bookingKey,
status
)=>{

await update(
ref(
db,
"bookings/" +
uid +
"/" +
bookingKey
),
{
status:status
}
);

};

window.deleteBooking = async (
uid,
bookingKey
)=>{

if(!confirm("Delete Booking?"))
return;

await remove(
ref(
db,
"bookings/" +
uid +
"/" +
bookingKey
)
);

};

window.loadAdminBookings = ()=>{

onValue(
ref(db,"bookings"),
(snapshot)=>{

let html = "";
let count = 0;

snapshot.forEach((user)=>{

const uid = user.key;

user.forEach((booking)=>{

count++;

const d = booking.val();

html += `

<div class="card">

<h4>${d.bookingId}</h4>

<p>${d.name || ""}</p>

<p>${d.email || ""}</p>

<p>${d.city}</p>

<p>${d.phone}</p>

<p>${d.status}</p>

<button
onclick="
changeStatus(
'${uid}',
'${booking.key}',
'Approved'
)
">
Approve
</button>

<button
onclick="
changeStatus(
'${uid}',
'${booking.key}',
'Rejected'
)
">
Reject
</button>

<button
onclick="
deleteBooking(
'${uid}',
'${booking.key}'
)
"
style="background:red;">
Delete
</button>

</div>

`;

});

});

document.getElementById(
"totalBookings"
).innerText =
"Total Bookings: " + count;

document.getElementById(
"adminData"
).innerHTML = html;

});

};

</script>
