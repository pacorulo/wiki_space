Use a delimiter and get string N, to finally put it in a file
```
cat ini.txt | cut -d '>' -f2 > target.txt
```
```
cat ini.txt | cut -d '>' -f2 | cut -d '<' -f 1 > final.txt
```
* f1 gets what is before the string
* f2 gets what is after the string

If we want to get the users in our pc:
```
cat /etc/passwd | cut -d ":" -f 1
```
