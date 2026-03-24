# 📂 WordlistsAllTheThings

![GitHub Stars](https://img.shields.io/github/stars/iamshafayat/WordlistsAllTheThings?style=flat-square&color=yellow)
![GitHub Forks](https://img.shields.io/github/forks/iamshafayat/WordlistsAllTheThings?style=flat-square&color=orange)
![Maintained](https://img.shields.io/badge/Maintained-yes-green?style=flat-square&color=00d4aa)
![For](https://img.shields.io/badge/For-Security%20Research-green?style=flat-square&color=00d4aa)

> A curated, well-organized collection of wordlists and payloads for bug bounty hunting and web application security testing. Gathered from various security researchers and organized for efficient use.

---

## ⚡ What's Inside

This repository contains wordlists for:

- **Directory & Path Fuzzing** — Common crawl data, dicc, general fuzzing lists
- **Vulnerability Payloads** — SQLi, XSS, LFI, SSRF, SSTI, CRLF, Open Redirect, Directory Traversal
- **Sensitive File Discovery** — Config files, env files, backup files, leaked files
- **Technology-Specific Wordlists** — WordPress, PHP, Apache, Nginx, IIS, Spring Boot, AEM, Grafana, Kibana, and more
- **API & Parameter Fuzzing** — API routes, parameter names
- **Authentication** — Default credentials, username lists
- **DNS & VHosts** — Subdomain and virtual host enumeration
- **Admin Panel Discovery** — Admin paths and panel finders
- **403 Bypass** — Header and URL-based bypass payloads
- **Git Exposure** — Git paths, config files, GitHub dorks
- **JWT** — JWT secret wordlists
- **Image Payloads** — SVG-based XSS, open redirect, pixel flood payloads
- **Mega/Combined Lists** — `onelistforall`, `everything`, `fuzz` variants for broad coverage

---

## 🗂️ Folder Breakdown

### `403-bypass/`
Payloads for bypassing 403 Forbidden responses via HTTP headers and URL manipulation.

### `admin/`
Wordlists for discovering admin panels, login pages, and admin-specific paths.

### `api/`
API endpoint wordlists including a large HTTP Archive dataset of real-world API routes.

### `commoncrawl_wordlist/`
Extension-specific wordlists derived from Common Crawl data. Compressed `.gz` files organized by file extension (php, asp, js, json, sql, zip, etc.). Large files are split into parts.

### `dns/`
DNS subdomain enumeration wordlist and virtual host (vhost) discovery list.

### `git/`
Wordlists and dorks for discovering exposed `.git` directories, config files, and sensitive Git data.

### `Image-Payloads/`
Malicious image files for testing upload vulnerabilities — includes SVG-based XSS, open redirect payloads, and pixel flood/DoS images.

### `jwt/`
Common JWT secret keys used for cracking weak JSON Web Token signatures.

### `parameter/`
Parameter name wordlists for fuzzing GET/POST parameters and finding hidden inputs.

### `payloads/`
Categorized attack payloads:

| Subfolder | Description |
|---|---|
| `auth/` | Default credentials and username lists — see usage below |
| `crlf/` | CRLF injection payloads |
| `directory_traversal/` | Path traversal for Unix and Windows |
| `lfi/` | Local File Inclusion payloads (small/large) |
| `redirect/` | Open redirect payloads |
| `sqli/` | SQL injection — MySQL, MSSQL, Oracle, PostgreSQL, blind, time-based, WAF bypass |
| `ssrf/` | Server-Side Request Forgery payloads |
| `ssti/` | Server-Side Template Injection payloads |
| `xss/` | Cross-Site Scripting — tags, event handlers, polyglots, WAF bypass, PortSwigger lists |
| `bambda.txt` | Burp Suite Bambda filter scripts |
| `extensions.txt` | File extension list for fuzzing |

### `sensitive-files/`
Wordlists for discovering sensitive and juicy files on web servers:
- Config files, `.env`, `.htaccess`, `phpinfo`, `phpmyadmin`
- Backup files, leaked file paths
- `robots-paths.txt` — paths commonly found in robots.txt

### `technologies/`
Technology-specific wordlists for targeted fuzzing:

| Folder | Technology |
|---|---|
| `aem/` | Adobe Experience Manager |
| `android/` | Android permissions |
| `apache/` | Apache HTTP Server |
| `aspx/` | ASP.NET / ASMX |
| `cgi/` | CGI-bin paths |
| `grafana/` | Grafana dashboard paths |
| `iis/` | Microsoft IIS |
| `iis-shortnameguesser-wordlist/` | IIS short name guesser (split archive) |
| `jsf/` | JavaServer Faces |
| `jsp/` | JavaServer Pages |
| `kibana/` | Kibana dashboard paths |
| `nginx/` | Nginx config paths |
| `perl/` | Perl scripts |
| `php/` | PHP paths and special files |
| `spring-boot/` | Spring Boot actuator endpoints |
| `swagger-ui/` | Swagger UI paths |
| `symfony/` | Symfony framework paths |
| `wordpress/` | WordPress core, plugins, backup files |

### Root-level Files
| File | Description |
|---|---|
| `1.txt` | General wordlist |
| `all_attacks.txt` | Combined attack payloads |
| `all_fuzz.txt` | Combined fuzzing wordlist |
| `dicc.txt` | General directory/path fuzzing list |
| `everything.txt` / `everything2.txt` | Mega combined wordlists |
| `fuzz.txt` / `fuzz2.txt` / `fuzzing_list.txt` | General purpose fuzzing lists |
| `nuclei-tags.txt` | Nuclei template tag list |
| `onelistforall.txt` | The ultimate combined wordlist |
| `onelistforallmicro.txt` | Micro version of onelistforall |
| `onelistforallshort.txt` | Short version of onelistforall |
| `xml.txt` / `yml.txt` / `zip.txt` | Extension-specific path wordlists |

---

## 🛠️ Usage Examples

**Directory fuzzing with ffuf:**
```bash
ffuf -u https://target.com/FUZZ -w WordlistsAllTheThings/onelistforallshort.txt
```

**XSS fuzzing:**
```bash
ffuf -u "https://target.com/search?q=FUZZ" -w WordlistsAllTheThings/payloads/xss/xss-small.txt
```

**SQLi testing with sqlmap:**
```bash
sqlmap -u "https://target.com/?id=1" --tamper-scripts-from WordlistsAllTheThings/payloads/sqli/
```

**Admin panel discovery:**
```bash
ffuf -u https://target.com/FUZZ -w WordlistsAllTheThings/admin/admin-panel-paths.txt
```

**Sensitive file discovery:**
```bash
ffuf -u https://target.com/FUZZ -w WordlistsAllTheThings/sensitive-files/juicy-paths.txt
```

**Technology-specific (WordPress):**
```bash
ffuf -u https://target.com/FUZZ -w WordlistsAllTheThings/technologies/wordpress/wp-fuzz-special.txt
```

**DNS subdomain enumeration:**
```bash
ffuf -u https://FUZZ.target.com -w WordlistsAllTheThings/dns/dns-wordlist.txt
```

**403 bypass:**
```bash
ffuf -u https://target.com/admin -H "FUZZ" -w WordlistsAllTheThings/403-bypass/403_header_payloads.txt
```

**Extract usernames & passwords from default credentials list:**
```bash
curl -s "https://raw.githubusercontent.com/iamshafayat/WordlistsAllTheThings/main/payloads/auth/default-username-password.txt" | cut -d":" -f1 | tee -a username.txt && curl -s "https://raw.githubusercontent.com/iamshafayat/WordlistsAllTheThings/main/payloads/auth/default-username-password.txt" | cut -d":" -f2 | tee -a password.txt
```

---

## ⚠️ Legal Disclaimer

> This repository is intended **strictly for authorized security testing, bug bounty programs, and educational purposes only.**
>
> Do **NOT** use these wordlists against systems you do not own or have explicit written permission to test. Unauthorized use of these tools against systems is **illegal** and unethical.
>
> The author of this repository takes **no responsibility** for any misuse or damage caused by the content in this repository. Always operate within the scope of your authorization.

---

## 🤝 Contributing

Found a useful wordlist that's missing? Contributions are welcome!

1. Fork the repository
2. Add your wordlist to the appropriate folder
3. Submit a pull request with a brief description of the source and use case

---

## ⭐ Credits

Wordlists collected and organized from various security researchers and public resources across the community. If you recognize your work here, thank you for your contribution to the security community.

---

*Happy Hunting! 🐛*