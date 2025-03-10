#networking 

Session hijacking is when an attacker takes control of an active session between a user and a website, usually by stealing the **session cookie**.

**How it works:**  
When you log into a website, the site often gives you a session cookie to remember you. If an attacker manages to steal this session cookie (through **[[Packet Sniffing]]**, **[[Cross-Site Scripting (XSS)]]**, or other methods), they can use it to **impersonate** you and take over your session, even without your login credentials.

**Example:**  
You’re logged into your online banking account. The attacker intercepts your session cookie and uses it to log into your account, performing actions like transferring money or viewing sensitive information, all without needing your username or password.