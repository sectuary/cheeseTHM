# FFUF Directory Fuzzing with Clean Output

## Basic Command
```bash
ffuf -u "http://10.10.2.151/FUZZ" -w /usr/share/wordlists/dirb/big.txt -t 50 -e .php -mc 200,301,302,403 -fs 276 -s | while IFS= read -r line; do echo "Found: http://10.10.2.151/$line | Status: $(curl -sI "http://10.10.2.151/$line" | head -n1 | cut -d' ' -f2)"; done
```
