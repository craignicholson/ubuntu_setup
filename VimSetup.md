# VIM Setup
Install Go{golang} First
 

## VIM

```shell

sudo apt-get install vim
sudo apt-get install vim-gnome

```


## Vim-Go setup
Read the documentation first rather than copy and paste and run... if you want to troubleshoot.  

https://github.com/fatih/vim-go

Another 15 minutes worth of reading and watching  
https://coolaj86.com/articles/getting-started-with-golang-and-vim/

Another one - using neo... for intelli-sense which failed to work but I got
a sweet color scheme.  

## Install pathogen - bundle managment

```shell

mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim

```
## Install vim-sensible
A set of vim defaults - this might not be needed for golang

```shell

git clone git://github.com/tpope/vim-sensible.git ~/.vim/bundle/vim-sensible

```

## Install syntastic
A syntax checker... this might not be needed for golang

```shell
git clone https://github.com/scrooloose/syntastic.git ~/.vim/bundle/syntastic

```


## Install airline

```shell

git clone https://github.com/bling/vim-airline ~/.vim/bundle/vim-airline

```
## Install NeoComplete
I chose neocomplete over YouCompleteMe.

```shell

$ cd ~/.vim/bundle/
$ git clone https://github.com/Shougo/neocomplete.vim.git
$ ls
neocomplete.vim  syntastic  vim-airline  vim-go  vim-sensible

```
Validation everything is in the proper place

```shell
Check 
cd ~/.vim/autoload
pathogen.vim
cd
cd  ~/.vim/bundle; ls
syntastic  vim-go  vim-sensible

```

## Install YouCompleteMe (requires building)
Note: YCM for unbuntu says install Vundle
https://github.com/VundleVim/Vundle.vim#about
>> skipping Vundle, trying another route

```shell
git clone https://github.com/Valloric/YouCompleteMe.git ~/.vim/bundle/YouCompleteMe
cd  ~/.vim/bundle/YouCompleteMe/
git submodule update --init --recursive
cd  ~/.vim/bundle/YouCompleteMe/
-- The build script requires Python version >= 2.6 and < 3.0 
--Arg!

```

### Workaround for the python versions
I use Anaconda and this framework makes swithcing pything env easy:  
(anaconda/continium to manage python and all the sci-py stuff)  

```shell

$ conda create --name snakes python=2.7
$ source activate snakes
$ python version
$ python --version
Python 2.7.11 :: Continuum Analytics, Inc.
$ cd  ~/.vim/bundle/YouCompleteMe/
$ ./install.py 

```
### When the build is complete and the machine has recovered, go back to py 3.5
$ source deactivate
discarding /home/cnicholson/anaconda3/envs/snakes/bin from PATH


# Edit .vimrc file - Second Version
Recommended mappings  

```shell

vim ~/.vimrc

```


>> " plugins expect bash - not fish, zsh, etc
set shell=bash

" pathogen will load the other modules
execute pathogen#infect()

" we want to tell the syntastic module when to run
" we want to see code highlighting and checks when  we open a file
" but we don't care so much that it reruns when we close the file
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

" go commands recomended
" https://github.com/fatih/vim-go#mappings

au FileType go nmap <leader>r <Plug>(go-run)
au FileType go nmap <leader>b <Plug>(go-build)
au FileType go nmap <leader>t <Plug>(go-test)
au FileType go nmap <leader>c <Plug>(go-coverage)

au FileType go nmap <Leader>ds <Plug>(go-def-split)
au FileType go nmap <Leader>dv <Plug>(go-def-vertical)
au FileType go nmap <Leader>dt <Plug>(go-def-tab)

au FileType go nmap <Leader>gd <Plug>(go-doc)
au FileType go nmap <Leader>gv <Plug>(go-doc-vertical)

au FileType go nmap <Leader>gb <Plug>(go-doc-browser)

au FileType go nmap <Leader>s <Plug>(go-implements)

au FileType go nmap <Leader>i <Plug>(go-info)

au FileType go nmap <Leader>e <Plug>(go-rename)

" Settings - turn highlighting on
let g:go_highlight_functions = 1
let g:go_highlight_methods = 1
let g:go_highlight_structs = 1
let g:go_highlight_operators = 1
let g:go_highlight_build_constraints = 1

" Enable goimports to automatically insert import paths instead of gofmt:
let g:go_fmt_command = "goimports"

" Location List Navigation
map <C-n> :lne<CR>
map <C-m> :lp<CR>

" Syntastic, if slow remove govet and errcheck from go checkers
let g:syntastic_go_checkers = ['golint', 'govet', 'errcheck']
let g:syntastic_mode_map = { 'mode': 'active', 'passive_filetypes': ['go'] }

" neocomplete
g:neocomplete#enable_at_startup = 1

" we also want to get rid of accidental trailing whitespace on save
autocmd BufWritePre * :%s/\s\+$//e

" tell vim to allow you to copy between files, remember your cursor
" position and other little nice things like that
set viminfo='100,\"2500,:200,%,n~/.viminfo

" tell vim to display line numbers
set number

### Open the sample file and run :GoInstallBinaries
 Make sure $GOPATH is setup correctly before running this

:GoInstallBinaries


# references ...
Take a look at others .vimrc files on github next time before doing it yourself
