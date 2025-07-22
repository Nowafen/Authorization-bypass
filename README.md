## Authorization Bypass via Headers (Nuclei Templates)
###### Date: July 2025
###### Reference : [PortSwigger Academy](https://portswigger.net/web-security)
###### By MNM [Contact](https://t.me/GoSecurity)
<img width="1200" height="700" alt="Screenshot from 2025-07-21 02-30-51" src="https://github.com/user-attachments/assets/e015e96c-2537-4d46-b6c0-3b867d4292da" />

---

This repository provides 15 Nuclei templates for testing IP-based authorization bypass techniques. The logic is based on observing 401/403 responses and reattempting requests with different IP-related HTTP headers to test access control misconfigurations.

Inspired by concepts introduced in PortSwigger's research, these templates aim to detect weak IP filtering by injecting headers such as:

- `X-Forwarded-For`
- `X-Real-IP`
- `CF-Connecting-IP`
- `X-Originating-IP`
- and others...

Each `.yaml` file corresponds to a specific header and attempts to access protected resources by simulating a trusted IP address like `127.0.0.1`.

---

## Usage

Clone the repository:
```bash
git clone https://github.com/Nowafen/Authorization-bypass
```

Run Nuclei with one or all templates:
```bash
nuclei -u https://admin.doamin.tld  -t Authorization-bypass/ 
```

Recommended test:
```bash
cat allurls.txt | httpx -mc 401,403 | nuclei -t Authorization-bypass/ -no-httpx
```

---

## Notes

- These templates are for **educational and authorized testing only**.
- Effective against web servers that incorrectly trust client-supplied IP headers.
- Tested with Nuclei v3+.

---

  © MNM – July 2025. Do not reproduce or republish without permission.

