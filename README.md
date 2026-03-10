# Ex03 To-Do List using JavaScript
## Date:10/3/2026

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
## index.html
```
<!DOCTYPE html>
<html>
<head>
<title>Advanced To-Do List</title>
<link rel="stylesheet" href="style.css">
</head>

<body>

<div class="container">

<h1>My Smart To-Do List</h1>

<div class="input-section">
<input type="text" id="taskInput" placeholder="Enter task...">
<button onclick="addTask()">Add</button>
</div>

<ul id="taskList"></ul>

<p id="taskCount">Tasks: 0</p>

</div>

<script src="script.js"></script>

</body>
</html>
```
## style.css
```
body{
font-family: Arial;
background: linear-gradient(120deg,#89f7fe,#66a6ff);
display:flex;
justify-content:center;
align-items:center;
height:100vh;
}

.container{
background:white;
padding:30px;
border-radius:10px;
width:400px;
box-shadow:0 10px 20px rgba(0,0,0,0.2);
}

h1{
text-align:center;
}

.input-section{
display:flex;
gap:10px;
}

input{
flex:1;
padding:10px;
border:1px solid #ccc;
border-radius:5px;
}

button{
padding:10px;
border:none;
background:#007bff;
color:white;
border-radius:5px;
cursor:pointer;
}

li{
display:flex;
justify-content:space-between;
align-items:center;
background:#f4f4f4;
padding:10px;
margin-top:10px;
border-radius:5px;
}

.completed{
text-decoration: line-through;
color:gray;
}

.actions button{
margin-left:5px;
padding:5px 8px;
}

.delete{
background:red;
}

.edit{
background:orange;
}

.complete{
background:green;
}
```
## script.js

```
let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

function renderTasks(){

let list = document.getElementById("taskList");
list.innerHTML="";

tasks.forEach((task,index)=>{

let li=document.createElement("li");

let span=document.createElement("span");
span.textContent=task.text;

if(task.completed){
span.classList.add("completed");
}

span.onclick=function(){
tasks[index].completed=!tasks[index].completed;
saveTasks();
}

let actions=document.createElement("div");
actions.className="actions";

let editBtn=document.createElement("button");
editBtn.textContent="Edit";
editBtn.className="edit";

editBtn.onclick=function(){
let newTask=prompt("Edit task",task.text);
if(newTask){
tasks[index].text=newTask;
saveTasks();
}
}

let deleteBtn=document.createElement("button");
deleteBtn.textContent="Delete";
deleteBtn.className="delete";

deleteBtn.onclick=function(){
tasks.splice(index,1);
saveTasks();
}

actions.appendChild(editBtn);
actions.appendChild(deleteBtn);

li.appendChild(span);
li.appendChild(actions);

list.appendChild(li);

});

document.getElementById("taskCount").textContent="Tasks: "+tasks.length;
}

function addTask(){

let input=document.getElementById("taskInput");

if(input.value===""){
alert("Enter task");
return;
}

tasks.push({
text:input.value,
completed:false
});

input.value="";

saveTasks();
}

function saveTasks(){
localStorage.setItem("tasks",JSON.stringify(tasks));
renderTasks();
}

renderTasks();
```

## OUTPUT
<img width="1889" height="897" alt="image" src="https://github.com/user-attachments/assets/8e305e67-ef2d-49df-aa53-cfd0560699fd" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
