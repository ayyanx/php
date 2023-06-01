# php
<?php
if (isset($_POST['submit'])) {
    // Get the remote file URL from the input field
    $remoteFileUrl = $_POST['remote_file_url'];

    // Generate a local file name for saving
    $localFileName = basename($remoteFileUrl);

    // Set the local file path for saving
    $localFilePath = __DIR__ . '/downloads/' . $localFileName;

    // Download the remote file and save it locally
    if (file_put_contents($localFilePath, file_get_contents($remoteFileUrl))) {
        echo "File downloaded and saved successfully!";
    } else {
        echo "Failed to download the file.";
    }
}
?>

<!DOCTYPE html>
<html>
<head>
    <title>Remote File Downloader</title>
</head>
<body>
    <h2>Remote File Downloader</h2>
    <form method="post" action="<?php echo $_SERVER['PHP_SELF']; ?>">
        <label for="remote_file_url">Remote File URL:</label>
        <input type="text" name="remote_file_url" id="remote_file_url" required>
        <br><br>
        <input type="submit" name="submit" value="Download">
    </form>
</body>
</html>

