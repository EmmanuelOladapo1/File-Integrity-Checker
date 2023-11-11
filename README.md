<h1>File Integrity Checker</h1>

 

<h2>Description</h2>
The project consists of downloading a Kali-Linux 32-bit package and writing code that checks the SHA256 value of the downloaded file. 
By comparing the SHA256 value of the downloaded package with the original package we can see if the file has been altered.  
<br />


<h2>Languages and Utilities Used</h2>

- <b>Pycharm</b> 
- <b>Python</b>
- <b>Web browser</b>


<h2>Environments Used </h2>

- <b>Pycharm</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Check the SHA256 value of the kali-linux 32-bit package and download: <br/>
<img src="https://i.postimg.cc/dVwmnXmb/Screenshot-2023-11-11-133125.png" height="80%" width="80%" alt="Checking and SHA256 value and downloading"/>
<br />  
<br />
Placed the Kali Linux package in a folder called testsha:  <br/>
<img src="https://i.postimg.cc/tTjXV3HN/Screenshot-2023-11-11-133747.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> 
<br />
Enabling operating systems and hashlibe functions: <br/>
<img src="https://i.postimg.cc/c1fFmQG8/Screenshot-2023-11-11-134156.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />import os: This line imports the os module, which stands for "operating system." 
  The os module provides a way of interacting with the operating system, allowing you to perform tasks such as file and directory operations, access environment variables, and execute system commands.
<br /> import hashlib: This line imports the hashlib module, which provides a common interface to various secure hash and message digest algorithms. Hash functions take an input (or 'message') and return a fixed-size string of bytes, which is typically a hash value

Calculating and returning the value of the kali linux package installed in the testsha folder :  <br/>
<img src="https://i.postimg.cc/LsqgmKtg/File-integrity-checker-part2-python-project.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> def calculate_sha256(file_path):: This line defines a function named calculate_sha256 that takes one parameter, file_path, representing the path to the file for which the SHA-256 hash needs to be calculated.

sha256_hash = hashlib.sha256(): This line initializes a SHA-256 hash object using the hashlib module. The sha256() function returns a new SHA-256 hash object.

with open(file_path, "rb") as f:: This line opens the file specified by file_path in binary mode ("rb"), creating a file object f. The with statement is used to ensure that the file is properly closed after reading, even if an error occurs during the file processing.

while True:: This starts an infinite loop. The code will break out of this loop when the end of the file is reached.

data = f.read(65536): This line reads a chunk of data (65536 bytes or 64 KB in this case) from the file and assigns it to the variable data.

if not data: break: If there is no more data to read (i.e., the end of the file has been reached), the loop is exited.

sha256_hash.update(data): This line updates the SHA-256 hash object with the current chunk of data.

return sha256_hash.hexdigest(): Once the entire file has been read and processed, the function returns the hexadecimal digest of the hash calculated from the file's contents using the hexdigest() method. The resulting hash is a string representing the SHA-256 hash value of the file.

In summary, this function calculates the SHA-256 hash of a file by reading it in chunks, updating the hash object with each chunk, and finally returning the hexadecimal digest of the overall hash.

<br />
Checking the integrity of the file and retunring the SHA256 value :  <br/>
<img src="https://i.postimg.cc/3NPYjVyV/File-Integrity-Checker-part-3-python-project.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />if not os.path.exists(directory_path) or not os.path.isdir(directory_path):: This line checks if the specified directory_path does not exist or is not a directory. If either condition is true, it prints an error message indicating that the directory does not exist and returns from the function.

for root, dirs, files in os.walk(directory_path):: This line uses os.walk to iterate through all the files and directories within the specified directory and its subdirectories. os.walk returns a tuple for each iteration, containing the root directory path, a list of subdirectories (dirs), and a list of files (files) in the current directory.

for file_name in files:: This line iterates through the list of files in the current directory.

file_path = os.path.join(root, file_name): This line creates the full path to the current file by joining the root directory path and the file name.

calculated_hash = calculate_sha256(file_path): This line calls the calculate_sha256 function (presumably defined elsewhere in the code) to calculate the SHA-256 hash of the current file.

print(f"File: {file_path}\nSHA-256 Hash: {calculated_hash}"): This line prints the file path and its corresponding SHA-256 hash.

In summary, the check_integrity function traverses through all the files in the specified directory and its subdirectories, calculates the SHA-256 hash for each file using the calculate_sha256 function, and prints the file path along with its corresponding hash value. 





<br />
Checking that this Python script is the main one:  <br/>
<img src="https://i.postimg.cc/HsR9526M/File-Integrity-Checker-part-4-python-project.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />if __name__ == "__main__":: This condition checks if the special variable __name__ is set to "__main__". In Python, when a script is executed, the __name__ variable is set to "__main__" if it is the main program being run. If the script is imported as a module into another script, __name__ is set to the name of the module.

The indented code block below the if __name__ == "__main__": statement is the code that will be executed only if the script is the main program.

directory_to_check = input("Enter the directory path to check integrity: "): This line prompts the user to enter a directory path through the console. The entered path is stored in the variable directory_to_check.

check_integrity(directory_to_check): This line then calls the check_integrity function (presumably defined elsewhere in the script) with the user-provided directory path as an argument. This function likely performs some form of integrity check on the files within the specified directory.

In summary, this block of code is a common pattern in Python scripts. It allows the script to be used both as a standalone program and as a module that can be imported into other scripts without automatically executing the contained code. If the script is being run directly, it prompts the user for a directory path and then calls a function to check the integrity of files in that directory.

<br />
Final outcome :  <br/>
<img src="https://i.postimg.cc/FKdRSynY/File-Integrity-Checker-part-5-python-project.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br /> When the code is run, it prompts the user to enter the filepathway where the file is saved. From the output we can tell that the file has not been altered as the SHA256 value for the orginal and downloaded file match. 
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
