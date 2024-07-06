# webpage-for-last-robot-movement
creating another webpage that displays the last robot movement 

I will create another webpage to check the last robot movement from the database then display it in the webpage 

i started creating the webpage by creating a new php file in the folder 'robot_control' which is called last.movement.php then writing a code that checks the last movement from the database and displays it in a new webpage 


![Screenshot 2024-07-06 204238](https://github.com/FaisalBaqutyan/webpage-for-last-robot-movement/assets/174335196/dfa41fd1-b088-49d5-9257-13e78688b806)


here is the code 

```
<?php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "robot_control";

// Create connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

// here i will select the last movement from the database 
$sql = "SELECT direction FROM movements ORDER BY id DESC LIMIT 1";
$result = $conn->query($sql);

$last_movement = "No movements recorded yet";

if ($result->num_rows > 0) {
    $row = $result->fetch_assoc();
    $last_movement = $row['direction'];
}

$conn->close();
?>

<!DOCTYPE html>
<html>
<head>
    <title>Last Robot Movement</title>
</head>
<body>
    <h1>Last Robot Movement</h1>
    <p>The last movement command was: <strong><?php echo $last_movement; ?></strong></p>
</body>
</html>
```

Then i opened a new web browser and write http://localhost/robot_control/last_movement.php 

and this is the new webpage that i created 

![Screenshot 2024-07-06 204940](https://github.com/FaisalBaqutyan/webpage-for-last-robot-movement/assets/174335196/5d549c72-f2e1-46ae-a83e-679436b18522)


and it changes every time i click a new movement in the first webpage 

![Screenshot 2024-07-06 204958](https://github.com/FaisalBaqutyan/webpage-for-last-robot-movement/assets/174335196/7b5be7e3-6b54-4dce-8f9e-d6b2fb16264e)


