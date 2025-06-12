# Notes
//it can other name dot zip replace with direct link ,.................... .............  .... ................ ...

file_put_contents('backup.zip', fopen('DIRECT_LINK', 'r'));
<?php 
$result='';


if ($_SERVER["REQUEST_METHOD"] === "POST") {
    $url = isset($_POST['url']) ? trim($_POST['url']) : '';
    $name = isset($_POST['d_name']) ? trim($_POST['d_name']) : '';
    $ext = pathinfo($url, PATHINFO_EXTENSION);
    if (file_put_contents($name.'.'.$ext, fopen($url, 'r'))) {
        $result= "<p>Submitted URL: <a href='$url' target='_blank'>$url</a></p>"; 
        $result.= "<p style='color: green;font-size:20px'>Download Success!</p>";
    } else { 
        $result= "<p style='color: red;'>Download Failed</p>";
    }
}

?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>URL Submission Form</title>
    <style>
        
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        form {
            background: #fff;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            padding: 20px;
            max-width: 400px;
            width: 100%;
        }
        h1 {
            font-size: 1.5rem;
            color: #333;
            text-align: center;
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-weight: bold;
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 4px;
            font-size: 1rem;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <form method="POST" action="">
        <h1>Enter a URL</h1>
        <label for="url">URL:</label>
        <input type="text" name="url" id="url" placeholder="Enter a valid URL" required>

        <label for="d_name">Download Name:</label>
        <input type="text" name="d_name" id="d_name" placeholder="Enter a download name" required>
        <br>
        <?php
        echo $result;
         ?>
        <button type="submit">Submit</button>
    </form>
    
</body>
</html>


  
