# File Upload Vulnerabilities

## What are File Upload Vulnerabilities
File upload vulnerabilities occur when an application allows users to upload files without properly validating the file’s type, content, or name, allowing attackers to upload malicious files.

## Impact of File Upload Vulnerabilities
-  Injection of malicious code.
-  Remote code execution.
-  Malware distribution.
-  Unauthorized access to sensitive data.
-  Full system compromise.

## Common Patterns
-  File upload directory with executable permission.
-  Validation based only on file extensions.
-  Lack of file content verification.
-  Reliance on client-side file validation.

## Example Attack Scenario
An attacker uploads a malicious script disguised as a legitimate file (e.g. shell.php.jpg). If the server executes the uploaded file, the attacker gains remote command execution.

## Remediation
-  Isolate file uploads from main components of the system.
-  Ensure uploaded files are not executed.
-  Rename files on upload.
-  Validate file format and extensions using allowlists.
-  Use antivirus/malware scanner on files.
-  Enforce file size limits.
-  Sanitize file names.
-  Be aware of compressed files.

## Key Lessons
-  File upload is a high-risk feature.
-  Proper server-side validation and isolation are critical for secure file handling.
