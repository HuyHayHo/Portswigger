# Lab: File path traversal, validation of start of path
 This lab contains a path traversal vulnerability in the display of product images.

The application transmits the full file path via a request parameter, and validates that the supplied path starts with the expected folder.

To solve the lab, retrieve the contents of the `/etc/passwd` file. 

## Solution
1. Use Burp Suite to intercept and modify a request that fetches a product image. 
2. Modify the `filename` parameter, giving it the value: 
> `/var/www/images/../../../etc/passwd`
3. Observe that the response contains the contents of the `/etc/passwd` file.
> ![alt text](image.png) 