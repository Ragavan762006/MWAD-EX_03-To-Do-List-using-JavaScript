# MWAD-EX_03-To-Do-List-using-JavaScript
## Date:

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
### index.html
```

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Todo App with Filters</title>
<link rel="stylesheet" href="style.css">
</head>
<body>
<h1>Todo App</h1>
<div class="container">
<form id="todoForm">
<input type="text" id="todoInput" placeholder="Enter a task" required>
<button type="submit">Add</button>
</form>


<ul id="todoList"></ul>


<div class="filters">
<button data-filter="all" class="active">All</button>
<button data-filter="completed">Completed</button>
<button data-filter="pending">Pending</button>
</div>
</div>
<script src="script.js"></script>
</body>
</html>
```
### style.css
```
body { font-family: Arial, sans-serif; background: #f0f0f0; padding: 20px; }
h1 { text-align: center; }
.container { max-width: 500px; margin: 0 auto; background: #fff; padding: 20px; border-radius: 8px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
#todoForm { display: flex; gap: 10px; margin-bottom: 10px; }
input[type=text] { padding: 8px; flex: 1; }
button { padding: 8px; cursor: pointer; }
ul { list-style: none; padding: 0; margin: 0; }
li { display: flex; justify-content: space-between; align-items: center; padding: 8px; margin-bottom: 5px; border-radius: 4px; border: 1px solid #ddd; }
li.completed .taskText { text-decoration: line-through; opacity: 0.6; }
.options button { margin-left: 5px; padding: 4px 6px; border: none; border-radius: 4px; cursor: pointer; background: #1f2937; color: #fff; }
.options button:hover { opacity: 0.8; }
.filters { display: flex; justify-content: center; gap: 10px; margin-top: 10px; }
.filters button { padding: 6px 12px; border: 1px solid #1f2937; background: #1f2937; color: #fff; border-radius: 4px; cursor: pointer; }
.filters button.active { background: #34d399; border-color: #34d399; }
```
### script.js
```
const form = document.getElementById('todoForm');
const input = document.getElementById('todoInput');
const list = document.getElementById('todoList');
const filterButtons = document.querySelectorAll('.filters button');
let todos = [];
let filter = 'all';


function render() {
list.innerHTML = '';
todos.filter(todo => {
if(filter === 'all') return true;
if(filter === 'completed') return todo.completed;
if(filter === 'pending') return !todo.completed;
}).forEach(todo => {
const li = document.createElement('li');
li.className = todo.completed ? 'completed' : '';


const span = document.createElement('span');
span.textContent = todo.text;
span.className = 'taskText';
li.appendChild(span);


const optionsDiv = document.createElement('div');
optionsDiv.className = 'options';


const completeBtn = document.createElement('button');
completeBtn.textContent = 'Complete';
completeBtn.addEventListener('click', () => { todo.completed = !todo.completed; render(); });


const editBtn = document.createElement('button');
editBtn.textContent = 'Edit';
editBtn.addEventListener('click', () => {
const newText = prompt('Edit task:', todo.text);
if(newText !== null && newText.trim() !== '') { todo.text = newText.trim(); render(); }
});


const deleteBtn = document.createElement('button');
deleteBtn.textContent = 'Delete';
deleteBtn.addEventListener('click', () => { todos = todos.filter(t => t !== todo); render(); });


optionsDiv.appendChild(completeBtn);
optionsDiv.appendChild(editBtn);
optionsDiv.appendChild(deleteBtn);
li.appendChild(optionsDiv);


list.appendChild(li);
});
}


form.addEventListener('submit', function(e) {
e.preventDefault();
todos.push({ text: input.value.trim(), completed: false });
input.value = '';
render();
});


filterButtons.forEach(btn => {
btn.addEventListener('click', () => {
filterButtons.forEach(b => b.classList.remove('active'));
btn.classList.add('active');
filter = btn.dataset.filter;
render();
});
});
```
## OUTPUT
<img width="1919" height="1077" alt="image" src="https://github.com/user-attachments/assets/f42f696e-6463-4d6b-8f2a-404e399d106a" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
