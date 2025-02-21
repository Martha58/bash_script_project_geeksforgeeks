# Extracting Links from GeeksforGeeks Using a Bash Script
This project involves writing a simple Bash script to extract URLs from the GeeksforGeeks website and save them to a file. The script downloads the website’s HTML file, filters out all links, and stores them in a text file for later use.

# Steps

* Step 1: Create a Working Directory
First, create a new folder where the HTML file will be downloaded. This keeps things organized.

* Step 2: Navigate to the Folder
Move into the newly created folder. This is where the script will download and process the HTML file.

* Step 3: Download the Website’s HTML File
Use the wget command to download the GeeksforGeeks homepage along with its dependencies.

wget --page-requisites https://www.geeksforgeeks.org

This command downloads the HTML content and saves it in a new directory named www.geeksforgeeks.org.

* Step 4: Locate the Downloaded HTML File
Navigate into the www.geeksforgeeks.org directory. The downloaded HTML file will be saved as index.html.

* Step 5: Extract URLs from the HTML File
To extract all URLs that start with https://www.geeksforgeeks.org, use cat to read the file and grep to filter out the links:

cat index.html | grep -oP 'https://www.geeksforgeeks\.org[^" ]*' > url.txt

cat index.html reads the content of the HTML file.
grep -oP 'https://www.geeksforgeeks\.org[^" ]*' extracts all URLs that start with https://www.geeksforgeeks.org.
The extracted URLs are saved into url.txt.

* Step 6: Move the Extracted Links to the Main Directory
Since the extracted links are saved inside the www.geeksforgeeks.org directory, move url.txt to the main directory before deleting the folder.

mv url.txt /path/to/directory
This prevents the loss of extracted data when the temporary directory is removed.

* Step 7: Delete the Temporary Directory
Move out of the www.geeksforgeeks.org directory and delete it since the HTML file is no longer needed.

cd ..
rm -rf www.geeksforgeeks.org

* Additional Notes
The script was written using the Nano editor.

After writing the script, I made it executable using:

chmod +x script_name
The script was then executed with:

./script_name

This Bash script efficiently extracts all links from GeeksforGeeks and saves them in a text file while keeping the working directory clean.
