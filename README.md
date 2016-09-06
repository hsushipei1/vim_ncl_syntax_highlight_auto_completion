#在vim替NCL語法上色以及自動補齊
=====
本文說明如何在vim編輯器下使[NCL](http://www.ncl.ucar.edu/)的關鍵字具有highlight以及自動補齊(auto completion, 補齊resources, 函式, 各種括號, etc)。安裝的plugin主要有三個：(1)ncl.vim: NCL的syntax檔案，(2)ncl.dic: NCL自動補齊，(3)[AutoComplPop](https://github.com/vim-scripts/AutoComplPop):讓vim自動跳出自動補齊的選單，如果不裝AutoComplPop，則須以指令ctrl+p呼叫選單，(4)[autoclose](https://github.com/Townk/vim-autoclose):各種括號的自動補齊。
<br></br>

##__NCL語法上色__

輸入指令
```bash
mkdir -p ~/.vim/syntax && cd ~/.vim/syntax
```
```bash
wget http://www.ncl.ucar.edu/Applications/Files/ncl3.vim
```
```bash
mv ncl3.vim ncl.vim
```
```bash
vim ~/.vimrc
```
將以下三行貼入

>" for NCL syntax highlight<br/>
>au BufRead,BufNewFile *.ncl set filetype=ncl<br/>
>au! Syntax newlang source ~/.vim/syntax/ncl.vim <br/>

重新開啟終端機後，即可發現NCL的語法被上色囉！
<br></br>

##__NCL自動補齊__
```bash
mkdir -p ~/.vim/dictionary/ && cd ~/.vim/dictionary/
```
```bash
wget http://www.ncl.ucar.edu/Applications/Files/ncl.dic
```
```bash
vim ~/.vimrc
```
將以下五行貼入
>"Show NCL autocomplete menus.<br/>
>set complete-=k complete+=k " Add dictionary search (as per dictionary option)<br/>
>set wildmode=list:full<br/>
>set wildmenu<br/>
>au BufRead,BufNewFile *.ncl set dictionary=~/.vim/dictionary/ncl.dic<br/>

重新開啟終端機後，游標在不完整的NCL關鍵字後方按下**ctrl+p**即可出現補齊的選單。例如輸入printVar後按下ctrl+p即可出現選單並補齊成printVarSummary。

<br></br>
##__AutoComplPop*__
AutoComplPop是否安裝因人而異，其功能在於**自動**跳出自動補齊選單，否則必須自行以ctrl+p呼叫選單。
```bash
cd ~ && git clone https://github.com/vim-scripts/AutoComplPop.git
```

```bash
cd AutoComplPop/
```
```bash
mkdir -p ~/.vim/autoload/ && mkdir -p ~/.vim/doc/ && mkdir -p ~/.vim/plugin/
```
```bash
cp autoload/acp.vim ~/.vim/autoload/ && cp doc/acp.* ~/.vim/doc/ && cp plugin/acp.vim ~/.vim/plugin/
```
重新開啟終端機後，vim將自動跳出自動補齊選單
<br></br>

##__Autoclose*__

```bash
cd ~ && git clone https://github.com/Townk/vim-autoclose.git
```
```bash
mkdir -p ~/.vim/doc/ && mkdir -p ~/.vim/plugin/
```
```bash
cp doc/AutoClose.txt ~/.vim/doc/ && cp plugin/AutoClose.vim ~/.vim/plugin/
```
重新開啟終端機後，vim將自動補齊各種括號，例如輸入"("，vim會自動輸入")"並將游標置於兩括號之間。
<br></br>
有了以上的plugin，將使在vim內撰寫NCL程式更方便。
<br></br>
P.S.:其他語言的自動補齊，例如python語言可利用[pydiction](https://github.com/vim-scripts/Pydiction)搭配AutoComplPop

> Written with [StackEdit](https://stackedit.io/).)
