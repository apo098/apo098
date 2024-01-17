<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plagiarism Checker</title>
</head>
<body>
    <h1>NEW Plagiarism Checker</h1>
    <form id="plagiarismForm">
        <label for="document">Enter your document:</label><br>
        <textarea id="document" name="document" rows="6" cols="50"></textarea><br>
        <button type="button" onclick="checkPlagiarism()">Check Plagiarism</button>
    </form>
    <p id="result"></p>

    <script>
        function checkPlagiarism() {
            // Get the document content
            var documentContent = document.getElementById('document').value;

            // Send the content to the server for plagiarism check
            // You would typically use AJAX to send an HTTP request to the server
            // Here, I'm using a placeholder URL and assuming the server responds with JSON
            fetch('checkPlagiarism.php', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ document: documentContent }),
            })
            .then(response => response.json())
            .then(data => {
                // Display the result to the user
                document.getElementById('result').innerHTML = data.result;
            })
            .catch(error => {
                console.error('Error:', error);
            });
        }
    </script>
</body>
</html>
