# Hugoblog install - by Alan Santos 07/01/2021

## Get hugo

```
mkdir $HOME/src
cd $HOME/src
git clone https://github.com/gohugoio/hugo.git
```

## Install hugo

`cd hugoCGO_ENABLED=1 go install --tags extended`

## Get hugoblog and theme submodule

`git clone --recursive https://github.com/alansantosmg/hugoblog/hugoblog.git`

### if already have cloned

`git submodule update --init`

### if there are nested submodules

`git submodule update --init --recursive`

## References

https://gohugo.io/getting-started/installing/
https://www.vogella.com/tutorials/GitSubmodules/article.html

