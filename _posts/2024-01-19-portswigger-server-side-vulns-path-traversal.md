---
title: PortSwigger Labs - Server-Side Vulnerabilities - File path traversal, simple case
date: 2024-01-18 10:00:00 +/-0000
categories: [PortSwigger, Lab]
tags: [portswigger, lab]     # TAG names should always be lowercase
---

# PortSwigger Server-Side Vulnerabilties Labs - File path traversal, simple case
Hi there!
Today I'll be working through the Path Traversal Labs.
![Path Traversal Labs Description](/../assets/posts/2024-01-19-portswigger-server-side-vulns-path-traversal/path_traversal_labs_description.png)

## Primer on Path Traversal

Here is a little primer first on Path traversal.

Path Traversal AKA Directory Traversal.
is a vulnerability that enables an attacker to read, or even write, to files that he shouldn't normally have access to.
Path Traversal is mainly about exploiting the `../` sequence to go up the directory tree.

For Unix-based systems the sequence `../` is valid. For windows both sequences `../` and `..\` are valid.

Here is two examples, one for a Unix-based system, the other for a Windows machine
```
// Unix
https://insecure-website.com/loadImage?filename=../../../etc/passwd
// Windows
https://insecure-website.com/loadImage?filename=..\..\..\windows\win.ini
```

Now for the lab
## Lab
The lab is a shop.
![Lab Shop](/../assets/posts/2024-01-19-portswigger-server-side-vulns-path-traversal/lab_shop.png)

The images links look like a good place to start looking for Path Traversal.
![Image Link Inspect](/../assets/posts/2024-01-19-portswigger-server-side-vulns-path-traversal/lab_image_link_inspect.png)

Let's launch Burp Suite
Here is the normal request/response
![Normal Request/Response](/../assets/posts/2024-01-19-portswigger-server-side-vulns-path-traversal/lab_image_normal_request-response.png)

Let's replace the `5.jpg` with `../../../../../../../etc/passwd`.
![Successful Path Traversal Exploiting The Image Link](/../assets/posts/2024-01-19-portswigger-server-side-vulns-path-traversal/lab_path_traversal_success.png)

Lab solved!
![Lab Solved](/../assets/posts/2024-01-19-portswigger-server-side-vulns-path-traversal/lab_solved.png)