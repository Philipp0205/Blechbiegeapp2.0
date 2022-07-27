#software-note |  #linux #open-source #command-line #terminal

---
# How to install fasd 
```
sudo snap install fasd --beta
```

or 

```
sudo add-apt-repository ppa:aacebedo/fasd
sudo apt-get update
sudo apt-get install fasd
```

then 

vim ~/.bashrc

```
eval "$(fasd --init auto)"
```