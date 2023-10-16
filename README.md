# badshafaysal0.github.io

<?php
include('db.php');

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $title = $_POST['title'];
    $description = $_POST['description'];
    $link = $_POST['link'];
    $image_url = $_POST['image_url'];

    $sql = "INSERT INTO projects (title, description, link, image_url) VALUES ('$title', '$description', '$link', '$image_url')";

    if ($conn->query($sql) === TRUE) {
        echo "New project added successfully";
    } else {
        echo "Error: " . $sql . "<br>" . $conn->error;
    }
}
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Add Project</title>
</head>
<body>
    <h1>Add New Project</h1>
    <form method="post" action="<?php echo $_SERVER['PHP_SELF']; ?>">
        Title: <input type="text" name="title"><br>
        Description: <textarea name="description"></textarea><br>
        Link: <input type="text" name="link"><br>
        Image URL: <input type="text" name="image_url"><br>
        <input type="submit" value="Add Project">
    </form>
</body>
</html>
