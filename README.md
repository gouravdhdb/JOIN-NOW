<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hello Love - Minecraft Panel</title>
    <link rel="stylesheet" href="gp.css">
</head>
<body>
    <div class="container">
        <h1>Welcome to Hello Love ❤️</h1>
        <form id="joinForm">
            <label for="username">Enter your Minecraft Name:</label><br>
            <input type="text" id="username" name="username" placeholder="Steve123"><br><br>
            
            <label for="server">Select your Server:</label><br>
            <select id="server" name="server">
                <option value="survival">Survival</option>
                <option value="creative">Creative</option>
                <option value="skyblock">Skyblock</option>
            </select><br><br>
            
            <button type="submit">Join Now!</button>
        </form>
    </div>

    <script>
        const form = document.getElementById('joinForm');

        form.addEventListener('submit', function(event) {
            event.preventDefault();

            const username = document.getElementById('username').value;
            const server = document.getElementById('server').value;

            fetch('http://localhost:3000/save', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ username, server })
            })
            .then(response => response.text())
            .then(data => {
                alert(data);
            })
            .catch(error => {
                alert('Error saving data.');
                console.error(error);
            });
        });
    </script>
</body>
</html>
body {
    background-color: #1e1e1e;
    color: #d4d4d4;
    font-family: 'Courier New', Courier, monospace;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: #2c2c2c;
    padding: 30px;
    border: 3px solid #00ff00;
    border-radius: 10px;
    box-shadow: 0 0 15px #00ff00;
    text-align: center;
}

h1 {
    color: #00ff00;
    margin-bottom: 20px;
}

input, select {
    padding: 10px;
    margin-top: 10px;
    width: 80%;
    border: none;
    border-radius: 5px;
}

button {
    background-color: #00ff00;
    color: #000;
    padding: 10px 20px;
    border: none;
    margin-top: 20px;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #00cc00;
}
