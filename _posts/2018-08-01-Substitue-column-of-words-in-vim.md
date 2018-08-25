---
layout: post
title: "Substitue column of words in vim"
author: "Endless"
categories: journal
tags: [vim, sed, snippet]
image: vim.png
---

Today I needed to learn how to change the first work of every line to another word, actually I cant remember why I needed to do that, but heres the snippet anyway, 

- [shift] + v //select code block to change
- [shift] + : //execute control over this block 
- s/^[^:]+:/word:/ // subsitute from beginning of line all chars that are not a colon, and then include the colon then replace with ‘word’, and add the : back there.

or using sed, without needing to open the file

- sed -e ‘s/^[^:]+:/word:/’ <filename here>
  
  This and many more really helpful tricks for vim, can be found here,
  https://www.cs.oberlin.edu/~kuperman/help/vim/home.html

