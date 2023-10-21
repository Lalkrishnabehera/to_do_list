# to_do_list
new repository
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple To-Do List</title>
    <style>
        body {
    font-family: Arial, sans-serif;
}

.container {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

h1 {
    text-align: center;
}

#task-form {
    display: flex;
    margin-bottom: 10px;
}

#task {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px 0 0 5px;
}

#task:focus {
    outline: none;
}

button {
    padding: 10px 20px;
    border: 1px solid #ccc;
    border-radius: 0 5px 5px 0;
    cursor: pointer;
}

button:hover {
    background-color: #f0f0f0;
}

ul {
    list-style: none;
    padding: 0;
}

li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
}

li button {
    background-color: #ff6666;
    color: #fff;
    border: none;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
}

li button:hover {
    background-color: #e74c3c;
}

li span {
    flex: 1;
}

    </style>
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <div id="task-form">
            <input type="text" id="task" placeholder="Add a task">
            <button onclick="addTask()">Add</button>
        </div>
        <ul id="task-list"></ul>
    </div>

    <script>
        function addTask() {
    const taskInput = document.getElementById('task');
    const taskText = taskInput.value.trim();

    if (taskText === '') {
        alert('Please enter a task.');
        return;
    }

    const taskList = document.getElementById('task-list');
    const li = document.createElement('li');
    li.innerHTML = `
        <span>${taskText}</span>
        <button onclick="editTask(this)">Edit</button>
        <button onclick="deleteTask(this)">Delete</button>
    `;
    taskList.appendChild(li);
    taskInput.value = '';
}

function editTask(button) {
    const newTaskText = prompt('Edit the task:', button.parentElement.firstChild.textContent);
    if (newTaskText !== null) {
        button.parentElement.firstChild.textContent = newTaskText;
    }
}

function deleteTask(button) {
    const taskList = document.getElementById('task-list');
    taskList.removeChild(button.parentElement);
}
    </script>
</body>
</html>
