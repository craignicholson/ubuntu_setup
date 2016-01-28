# Setting up Go Workspace - ubuntu

Download Go
https://golang.org/dl/

tar -C /usr/local -xzf go1.5.2.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin

// put this export in the .bashrc file too


# Uninstall go - test this please - cnicholson, need to validate the code
rm -rf ~/usr/local/go


# setup env in home, because it's easy that way and all code goes to github now

$ mkdir gocode
$ export GOPATH=$HOME/gocode
$ export PATH=$PATH:$GOPATH/bin
$ cd gocode
gocode $ mkdir bin
gocode $ mkdir pkg
gocode $ mkdir -p src/github.com/yourgithubaccount
gocode $ cd  src/github.com/yourgithubaccount
craignicholson $ mkdir hello
craignicholson $ cd hello
hello $ vim hello.go

package main

import (
  "fmt"
)

func main() {
  fmt.Println("Hello, Craig")
}

:w
:q

cn hello $ go install
cn hello $ hello
cb hello $ Hello, Craig

/* Add GOPATH to .bash_profile
   You need to do this so the terminal has the paths cached
   when you load and run the code....

*/
cn $ cd
cn $ vim .bashrc (MAC is .bash_profile, ubuntu is .bashrc)
-- i for insert
export PATH=$PATH:/usr/local/go/bin
export GOPATH=$HOME/gocode
export PATH=$PATH:$GOPATH/bin
-- esc
:x!

# Test
$ go install github.com/yourgithubaccount/hello

$ cd 
$ ls
anaconda3         gocode        notebook     SystemBuild~   vim-pathogen
Desktop           Music         Pictures     Templates      VimSetup
Documents         netcat        Public       testFile.txt   VimSetup~
Downloads         netcat~       sketchbook   testFile.txt~
examples.desktop  netcat-0.7.1  SystemBuild  Videos

$ cd gocode/
$ ls
bin  pkg  src

$ cd bin
$ ls
errcheck  godef      golint        gorename  hello
gocode    goimports  gometalinter  gotags    oracle

//run the app
:~/gocode/bin$ hello
Hello, Craig


