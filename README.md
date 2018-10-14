# ToDoList-Project
A quick to-do list application that allows the user to add, cross off, and delete list items. 
This project focused primarily on CSS customization and jQuery event triggers. 

To look at the application copy the files into a folder and open index.html file. 

click on the "+" icon to toggle the add new field.
click on the task to strike off finished tasks, click on the delete which shows up when hovered over the task to delete.





















<html> 
<head> 

<script>
var stateObject = {
    "INDIA": {
        "Telangana": ["Hyderabad", "warangal"],
        "Andhrapradesh": ["guntur", "vijaywada"]
    },
    "USA": {
        "new jersey": ["jersey city", "newark"],
        "kansas": ["kansas", "rockville"]
    }
}
window.onload = function () {
    var countySel = document.getElementById("countySel"),
        stateSel = document.getElementById("stateSel"),
        districtSel = document.getElementById("districtSel");
    for (var country in stateObject) {
        countySel.options[countySel.options.length] = new Option(country, country);
    }
    countySel.onchange = function () {
        stateSel.length = 1; // remove all options bar first
        districtSel.length = 1; // remove all options bar first
        if (this.selectedIndex < 1) return; // done   
        for (var state in stateObject[this.value]) {
            stateSel.options[stateSel.options.length] = new Option(state, state);
        }
    }
    countySel.onchange(); // reset in case page is reloaded
    stateSel.onchange = function () {
        districtSel.length = 1; // remove all options bar first
        if (this.selectedIndex < 1) return; // done   
        var district = stateObject[countySel.value][this.value];
        for (var i = 0; i < district.length; i++) {
            districtSel.options[districtSel.options.length] = new Option(district[i], district[i]);
        }
    }
}


  function validateEmail()
      {
         var emailID = document.getElementById("email");


         atpos = emailID.indexOf("@");
         dotpos = emailID.lastIndexOf(".");
         
         if (atpos < 1 || ( dotpos - atpos < 2 )) 
         {document.write("emailID");
            alert("Please enter correct email ID")
            document.myForm.EMail.focus() ;
            return false;
         }
         return( true );
      }
   

</script>

<style>

h1{

padding-top:5%;
}
   
div {

    border: 10px  grey; 
    float: left; 
    align-content: center; 
    align-items: center; 
padding-bottom:5px;
padding-left:5px;

} 
.container {
  width: 500px;
  clear: both;
}
.container input {
  width: 100%;
  clear: both;
}   


form { 
                                        
    margin-left: 500 ; 

    width: 600px; 
}</style>
</head> 

<body>
<h1 style="text-align:center" >Registration Form</h1>
<form align="Left" onsubmit="validateEmail()">
<div class="container">
<div>First Name<input type="text" size=65 name="FName" placeholder="fname" required></div><br>
<div>Last Name <input type="text" size=65 name="LName" placeholder="Lname" required></div><br>
<div> Date of Birth<input type="date" size=65 name="Dob" placeholder="dob" required  ></div><br><br>
<div>Age <input type="text" size=70 name="age" placeholder="age" required ></div><br>
<div>Email <input type="text" size=69 name="email" id="email" placeholder="email" required onkeyup="validateEmail()"  ></div><br>
<div>Phonenumber <input type="number" size=65 name="Pnumber" placeholder="phnumber" min="999999999" max="10000000000" required ></div><br>
<div>Address <input type="text" size=65 name="Address" placeholder="address" required ></div><br>
<div>Select Country: <select name="state" id="countySel" size="1">
        <option value="" selected="selected">Select Country</option>
    </select>
    <br>
    <br>
    Select State: <select name="countrya" id="stateSel" size="1">
        <option value="" selected="selected">Please select Country first</option>
    </select>
    <br>
    <br>
    Select District: <select name="district" id="districtSel" size="1">
        <option value="" selected="selected">Please select State first</option>
    </select><br> 
</div>
<input type="submit">
</div>

</form>
</body>
