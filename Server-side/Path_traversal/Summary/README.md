# File path traversal, simple case
> `Basic Traversal`
- Use the `../` character to move up one level in the directory structure and access files beyond the target directory.
- For example: `../../../etc/passwd` to access the file `/etc/passwd`.

# File path traversal, traversal sequences blocked with absolute path bypass
> `Absolute Path Bypass`
- If the application blocks the `../` string, maybe try using an absolute path starting from the system root.
- For example: `/etc/passwd`.

# File path traversal, traversal sequences stripped non-recursively
> `non-recursively`
- If the application only filters the string `../` in a non-recursive manner, you can exploit it by repeating strings like `....//` multiple times to bypass the filtering mechanism.
- For example: `....//....//....//etc/passwd`

# File path traversal, traversal sequences stripped with superfluous URL-decode
> `Superfluous URL-Decode`
- If your application performs URL decoding multiple times before use, you can encode path traversal strings multiple times to avoid blocking.
- For example: `..%252f..%252f..%252fetc/passwd`

# File path traversal, validation of start of path
> `Start of Path Validation Bypass`
- An application may require the user-supplied filename to start with the expected base folder, such as `/var/www/images`. In this case, it might be possible to include the required base folder followed by suitable traversal sequences. 
- For example: `filename=/var/www/images/../../../etc/passwd`.

# File path traversal, validation of file extension with null byte bypass
> `Null Byte Injection`
- An application may require the user-supplied filename to end with an expected file extension, such as `.png`. In this case, it might be possible to use a null byte to effectively terminate the file path before the required extension
- For example: `filename=../../../etc/passwd%00.png`