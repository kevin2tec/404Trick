# 403Trick
Bypass 401/403 endpoints using smart fuzzing techniques  
Author: **kevinw3b**

`403Trick` is a smart bypassing toolkit that attempts to find access control flaws and URL validation weaknesses. It uses a variety of tricks such as:

- Header manipulation
- Path normalization
- HTTP verb tampering
- Smart filtering to reduce noise

Useful for bug bounty hunters and pentesters who want to automate 403/401 bypass techniques.

---

## ✨ Features

- Color-coded and organized response output
- Automatic deduplication of similar responses (smart filter)
- Support for raw HTTP requests (Burp-style)
- Request/response storage to a SQLite database
- Proxy support (e.g. Burp Suite)
- Easy filtering and replay of successful payloads
- Optional OOB/SSRF pingback testing

---

## 🐧 Linux & macOS Setup

```bash
git clone https://github.com/kevinw3b/403Trick.git
cd 403Trick
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
🪟 Windows Setup
bash
Copy
Edit
cd 403Trick
py -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
🚀 Usage
See help:

bash
Copy
Edit
python3 bypassfuzzer.py -h
🔥 Best Method: Use a Burp HTTP request
Paste a raw request into a file:

bash
Copy
Edit
python3 bypassfuzzer.py -r request.txt
URL-based Request
bash
Copy
Edit
python3 bypassfuzzer.py -u https://example.com/secret-page
🛠 Common Flags
Set HTTP method and data:

bash
Copy
Edit
-m POST -d "param1=value&param2=value"
Add headers:

bash
Copy
Edit
-H "Authorization: Bearer <token>"
Add cookies:

bash
Copy
Edit
-c "cookie1=value; cookie2=value"
Smart filter to mute repeated responses:

bash
Copy
Edit
--smart
Proxy through Burp:

bash
Copy
Edit
--proxy http://127.0.0.1:8080
Skip payload types:

bash
Copy
Edit
--skip-headers
--skip-urls
Hide response codes/lengths:

bash
Copy
Edit
-hc 403,404
-hl 638
🧠 View Successful Interactions
Each successful request (200 OK) is logged with an index. To display a request/response pair:

bash
Copy
Edit
# by index
--display-by index --display-interactions 12

# by payload
--display-by payload --display-interactions "/%2e%2e/"
You can specify a DB to query:

bash
Copy
Edit
--idb interactions_20240729_145149.db
🌐 OOB / Blind SSRF Pingback
Provide your OOB domain:

bash
Copy
Edit
--oob yourdomain.oastify.com
Note: You must monitor DNS/HTTP logs externally to confirm.

📌 TODO
 Add HTTP/2 support

 Support multiple simultaneous request sources

 Add CLI flags for smart filter tuning

 Community payload submission & tuning

☕ Support & Contact
If this tool helped you land a bounty or you'd like to support development:

Buy me a coffee: https://coff.ee/kevinw3b

DISCORD :kevinw3b