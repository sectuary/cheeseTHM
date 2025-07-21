# FFUF Directory Fuzzing with Clean Output

## Directory Bruteforcing
```bash
ip="10.10.2.151"; ffuf -u "http://$ip/FUZZ" -w /usr/share/wordlists/dirb/big.txt -t 50 -e .php -mc 200,301,302,403 -fs 276 -s | while IFS= read -r line; do echo "Found: http://$ip/$line | Status: $(curl -sI "http://$ip/$line" | head -n1 | cut -d' ' -f2)"; done

```
## SQL Injection test
```bash
ffuf -w sql_payload.txt -X POST -u http://10.10.2.151/login.php -d 'username=FUZZ&password=ANY' -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" -mc 301,302
```
