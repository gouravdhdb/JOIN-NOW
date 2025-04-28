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
