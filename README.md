Reflected XSS in HTML Context - Challenge Write-Up
Introduction
Welcome to the Reflected XSS in HTML Context challenge! In this room, you will delve into a classic Reflected Cross-Site Scripting (XSS) vulnerability. Your mission is to identify and exploit this vulnerability within the web application and capture the hidden flag. XSS attacks enable attackers to inject malicious client-side scripts into web pages, potentially leading to severe consequences for users.

In this lab, the HTML context does not apply any special encoding, making it particularly vulnerable to script injection.

Challenge Setup
You are presented with a basic web application that includes several features:

Home Page
Search Page (vulnerable)
About Us
Contact Us
The vulnerability resides in the Search Page, where user input is reflected back without proper sanitization. Your goal is to find this vulnerability, inject a malicious script, and retrieve the hidden flag.

Objective
Find the Reflected XSS vulnerability in the search feature of the web application. Trigger an alert box using a simple JavaScript injection, and reveal the hidden flag by exploiting this vulnerability.

Step-by-Step Solution
1. Inspect the Web Application
Begin by exploring the web application. Navigate to the Search page, where you will find an input field allowing users to search for terms. Input a simple search term and observe how the application reflects this input back in the HTML response.

2. Inject a Basic XSS Payload
The primary objective is to exploit the search field, which reflects user input into the HTML output without sanitization. To test this, inject a basic XSS payload:
<script>alert('XSS')</script>
Input this payload into the search field and submit the form. If the application is vulnerable, you should see a pop-up alert box displaying the message 'XSS', confirming the presence of the vulnerability.

3. Capture the Flag
Having confirmed the XSS vulnerability, the next step is to retrieve the hidden flag. Typically, flags are stored in cookies or sessions. To access this information, use the following XSS payload:
<script>alert(document.cookie)</script>
Inject this payload into the search field and submit the form. An alert box will display the contents of document.cookie, which should include the flag. The flag format will resemble:
flag{congrats_you_solved_it}
Remediation
To prevent XSS vulnerabilities in real-world applications, consider the following best practices:

Input Validation: Always validate and sanitize user input. Never trust user inputs blindly; ensure that special characters like <, >, &, etc., are properly encoded.
Output Encoding: Encode user inputs when reflecting them in the HTML context to prevent the execution of malicious scripts.
Content Security Policy (CSP): Implement CSP headers to restrict the execution of inline JavaScript, thereby reducing the risk of XSS attacks.
Utilize Secure Frameworks: Leverage modern frameworks or libraries that automatically manage input/output sanitization, such as React or Angular.
Conclusion
This challenge highlights the risk of Reflected XSS vulnerabilities in web applications. By adhering to best practices such as input validation, output encoding, and employing security headers like CSP, developers can significantly mitigate the risks associated with XSS vulnerabilities. Congratulations on successfully completing the challenge!

References
OWASP XSS Prevention Cheat Sheet
Mozilla Developer Network (MDN) - Cross-Site Scripting (XSS)
