# FFUF Directory Fuzzing with Clean Output

## Basic Command
```bash
ip="10.10.2.151"; ffuf -u "http://$ip/FUZZ" -w /usr/share/wordlists/dirb/big.txt -t 50 -e .php -mc 200,301,302,403 -fs 276 -s | while IFS= read -r line; do echo "Found: http://$ip/$line | Status: $(curl -sI "http://$ip/$line" | head -n1 | cut -d' ' -f2)"; done

```
