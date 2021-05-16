# HTB-misDIRection
Solution to misDIRection challenge on HackTheBox

After a few attempts, I figured out that I needed to sort each directory in `.secret`
by their files' names. Which led to this small shell script:
```sh
find .secret -type f | sort -t / -k 3,3 -n | cut -d/ -f2 | tr -d \\n | base64 -d
```

1. Print each file in .secret
2. Output is of form `.secret/<directory>/<file>`. Sort after the second `/`
3. Only keep the directory name
4. Remove new lines
5. Base64 decode the result
