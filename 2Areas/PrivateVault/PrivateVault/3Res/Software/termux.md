# Termux
#terminal #command-line 
[[!Software]]

---

# Git einrichten
`git config --global user.name "Philipp0205"`

`git config --global user.email "philipp.kurrle@gmail.com"`

# Autocommit

```
#!/bin/bash

CURRENTDATE=`date +"%Y-%m-%d %T"`
DATETIME=`date +"%Y-%m-%d %T"`

while true 
do 
  git pull 
  git add -A 
  git commit -m "${DATETIME}"
  git push origin master
  sleep 300
done
```

