---
title: Hide iTerm2's zsh notification
tags: mac
---
The preinstalled Terminal application on a Mac is very basic, at least for me. Thus, I installed [iTerm2](https://iterm2.com/) that provides a lot of features and functions I was missing; but for a long time now, the default shell in iTerm2 is [Z shell](https://en.wikpedia.org/wiki/Z_shell). However, I already configured my Bash and I don't plan to switch. So, what I need to do to avoid the notification "_The default interactive shell is now zsh_" every time I start a new session?  
The solution is very easy:  
1.) open the _.bash_profile_ in your home directory:  
```vi ~/.bash_profile ```  
2.) add the below line:  
```export BASH_SILENCE_DEPRECATION_WARNING=1```  

If you ever want to see the message again, just open the above file again and delete the extra line you just added.