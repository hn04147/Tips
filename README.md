# Tips
ðëì ëì  ì ì©í íë¤

<br />

1. [ë§¥ìì ë¶í  ìì¶ í¸ë ë°©ë²](#1-ë§¥ìì-ë¶í -ìì¶-í¸ë-ë°©ë²)  
2. [Mac í°ë¯¸ë iterm2 ì»¤ì¤í](#2-Mac-í°ë¯¸ë-iterm2-ì»¤ì¤í)  
3. [Sshë¡ remote server ì ì ì terminal ìê¹ ìíê¸°](#3-Sshë¡-remote-server-ì ì-ì-terminal-ìê¹-ìíê¸°)  
4. [Ssh ë¹ë°ë²í¸ë¡ ì ì ì¤ì íê¸°](#4-Ssh-ë¹ë°ë²í¸ë¡-ì ì-ì¤ì íê¸°)
5. [Sshë¡ remote server ì ì ì alias ê¸°ë³¸ì¼ë¡ ì¤ì  íê¸°](#5-Sshë¡-remote-server-ì ì-ì-alias-ê¸°ë³¸ì¼ë¡-ì¤ì -íê¸°)
6. [Sshë¡ remote server ì ì ì bashrc ê¸°ë³¸ì¼ë¡ ì¤ííê¸°](#6-Sshë¡-remote-server-ì ì-ì-bashrc-ê¸°ë³¸ì¼ë¡-ì¤ííê¸°)
7. [íì í´ëìì ìë íì¼ ê°ì ì¶ë ¥](#7-íì-í´ëìì-ìë-íì¼-ê°ì-ì¶ë ¥)
8. [Ssh ìë² íì¼ ìê²© ì ì¡íê¸°](#8-Ssh-ìë²-íì¼-ìê²©-ì ì¡íê¸°)
9. [íì´ì¬ ë¦¬ì¤í¸ íì íê¸°](#9-íì´ì¬-ë¦¬ì¤í¸-íì íê¸°)
10. [GPUì ë©ëª¨ë¦¬ë í ë¹ëì´ ìëë° nvidia-smiìë ìëì¬ ë](#10-GPUì-ë©ëª¨ë¦¬ë-í ë¹ëì´-ìëë°-nvidia-smiìë-ìëì¬-ë)

<br />

# 1. ë§¥ìì ë¶í  ìì¶ í¸ë ë°©ë²

1. ```zip -FF ë¶í ìì¶ëìë³¸íì¼ëª.zip --out íê°ë¡ìì¶ë íì¼ëª.zip```  
2. ```unzip -qt íê°ë¡ìì¶ë íì¼ëª.zip```  

> EX) íì¼ëªì´ ```data.zip```, ```data.z01```, ```data.z02``` ì´ë ê² ëì´ìì ë  
> 1. ```zip -FF data.zip --out data_concat.zip``` ì¼ë¡ ìì¶ íì¼ í©ì¹ê¸°
> 2. ```unzip -qt data_concat.zip``` ì¼ë¡ í©ì¹ íì¼ ìì¶ íê¸° 

<br />

# 2. Mac í°ë¯¸ë iterm2 ì»¤ì¤í

### oh-my-zsh ì­ì 
>ì´ì ì í°ë¯¸ëì ì»¤ì¤í í ì ì´ ìì´ Oh My Zshê° ì´ë¯¸ ê¹ë ¤ìë ìí©ì´ë¼ë©´ ìë ì½ëë¡ í°ë¯¸ë ì´ê¸°íë¥¼ ìì¼ì¤ë¤.
```javascript
rm -rf ~/.oh-my-zsh
rm ~/.zshrc
cp ~/.zshrc.pre-oh-my-szh ~/.zshrc
source ~/.zshrc
```

### ìëì½ë¤ zshìì ì¬ì©íë ë°©ë²
> .zshrcì ë¤ì´ê°ì íê²½ë³ì ì¤ì 
> ìë ì½ëë¤ì ì ì¼ ë°ì ì¶ê°í´ì£¼ì
```
vi ~/.zshrc      // .zshrc í¸ì§
                 // ìë ì½ë ì¶ê° 


export PATH=$HOME/bin:/usr/local/bin:/anaconda3:/anaconda3/bin:$PATH

# >>> conda initialize >>>
 # !! Contents within this block are managed by 'conda init' !!
 __conda_setup="$('/Users/Sangjin/opt/anaconda3/bin/conda' 'shell.zsh' 'hook'     2> /dev/null)"
 if [ $? -eq 0 ]; then
     eval "$__conda_setup"
 else
     if [ -f "/Users/Sangjin/opt/anaconda3/etc/profile.d/conda.sh" ]; then
         . "/Users/Sangjin/opt/anaconda3/etc/profile.d/conda.sh"
     else
         export PATH="/Users/Sangjin/opt/anaconda3/bin:$PATH"
     fi
 fi
 unset __conda_setup
 # <<< conda initialize <<<
```

<br />

# 3. Sshë¡ remote server ì ì ì terminal ìê¹ ìíê¸°
* ```~/.bashrc``` ì ìë ì½ëë¥¼ ì¶ê°í´ì¤ë¤.
```
# >>> enable color support of terminal directory >>>
export PS1="\[\e]0;\u@\h \w\a\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w #\[\033[00m\] "
# <<< enable color support of terminal directory <<<


# >>> enable color support of ls and also add handy aliases >>>
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
# <<< enable color support of ls and also add handy aliases <<<
```
* ì´í ```source ~/.bashrc``` ë¥¼ ì¤ííì¬ ì ì©ìì¼ì¤ë¤.

<br />

# 4. Ssh ë¹ë°ë²í¸ë¡ ì ì ì¤ì íê¸°

1. root ê¶íì¼ë¡ ```passwd root``` ë¥¼ ìë ¥íì¬ ```Enter new UNIX passwd``` ì ```Retype new UNIX passwd``` ì ëì¼í ë¹ë°ë²í¸ë¥¼ ìë ¥íë¤.
2. root ê¶íì¼ë¡ ```vim /etc/ssh/sshd_config``` ë¥¼ ìë ¥íì¬ ```/etc/ssh/sshd_config``` íì¼ì ì´ì´ì ```PasswordAuthentication yes``` ë¡ ë³ê²½ì í´ì¤ë¤.
3. ë§ì§ë§ì¼ë¡ root ê¶íì¼ë¡ ```service ssh restart```ë¥¼ íì¬ ssh ì¬ë¶íì ìì¼ì¤ë¤.
4. ì´í ```ssh root@<your ip> -p <your port>```ë¡ ì ìì íë©´ ì¤ì í ë¹ë°ë²í¸ë¥¼ ìë ¥íì¬ ì ìí  ì ìë¤.

<br />

# 5. Sshë¡ remote server ì ì ì alias ê¸°ë³¸ì¼ë¡ ì¤ì  íê¸°
* ```~/.bash_aliases``` ì ```alias`ë¥¼ ì ì©í  ì½ëë¥¼ ìì±í´ì¤ë¤.
```
alias ll='ls -al'
```
* ```~/.bashrc``` ì ìë ì½ëë¥¼ ì¶ê°í´ì¤ë¤.
```
# >>> enable '.bash_aliases' >>>
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
# <<< enable '.bash_aliases' <<<<
```

<br />

# 6. Sshë¡ remote server ì ì ì bashrc ê¸°ë³¸ì¼ë¡ ì¤ííê¸°
* ```~/.bash_profile``` íì¼ì ìì±íê³  ìë ì½ëë¥¼ ì¶ê°íë¤.
```
if [ -f ~/.bashrc ]; then 
  . ~/.bashrc 
cd ~
fi
```

<br />

# 7. íì í´ëìì ìë íì¼ ê°ì ì¶ë ¥
```
for x in `ls` ; do echo $x: `find $x -type f | wc -l`; done
```
ì¶ê°ë¡ ```~/.bash_aliases``` ì ```alias fn='for x in `ls` ; do echo $x: `find $x -type f | wc -l`; done'``` ë¥¼ ì¶ê°í´ì£¼ë©´ í¸íê² ```fn``` ëªë ¹ì´ë¡ ì¤íìí¬ ì ìë¤.

<br />

# 8. Ssh ìë² íì¼ ìê²© ì ì¡íê¸°
* Localìì sshë¡ íì¼ ì ì¡
```
scp -r {local ìë² ì£¼ì} {ssh ìë² ì£¼ì}
ex) scp -r root@118.67.131.239:/opt/ml/code /Users/Desktop/
```
* Sshìì localë¡ íì¼ ì ì¡
```
scp -r {ssh ìë² ì£¼ì} {local ìë² ì£¼ì}
ex) scp -r /Users/Download/a.txt root@118.67.131.239:/opt/ml/code
```
<br />

# 9. íì´ì¬ ë¦¬ì¤í¸ íì íê¸°
```
k = [[1, 2, 3],
     [4, 5, 6],
     [7, 8, 9]]

# ìê³ ë°©í¥ íì 
li = [list(k[::-1]) for k in zip(*k)]
# zipë¥¼ ì¨ì ê° ì¸ë±ì¤ì ëª¨ë  elementë¥¼ í iteratorì ë£ê³  asteriskë¥¼ ì´ì©íì¬ íì´ì íì  ìê³ ë¦¬ì¦ì êµ¬í
# ex) k = [[1, 2, 3],     ->   ìíë ì¶ë ¥ form: [[7, 4, 1],
#          [4, 5, 6],                          [8, 5, 2],
#          [7, 8, 9]]                          [9, 6, 3]]
# zip(*k) = [[1, 4, 7],
#            [2, 5, 8],
#            [3, 6, 9]]
print(li)

# ë° ìê³ ë°©í¥ íì 
li = [list(k) for k in reversed(tuple(zip(*k)))]
# ìê³ ë°©í¥ê³¼ ëì¼í ë°©ìì´ì§ë§, reversed í¤ìëë¥¼ ì¬ì©íì¬ ë°°ì´ì ì­ì íìì´ ê°ë¥íê² í¨
# ex) k = [[1, 2, 3],     ->   ìíë ì¶ë ¥ form: [[3, 6, 9],
#          [4, 5, 6],                          [2, 5, 8],
#          [7, 8, 9]]                          [1, 4, 7]]
# reversed(tuple(zip(*k))) = [[3, 6, 9],
#                             [2, 5, 8],
#                             [1, 4, 7]]
print(li)
```

<br />

# 10. GPUì ë©ëª¨ë¦¬ë í ë¹ëì´ ìëë° nvidia-smiìë ìëì¬ ë
```
for i in $(ps aux | grep python | awk '{print $2}' | sort -u); do kill -9 $i; done
```
