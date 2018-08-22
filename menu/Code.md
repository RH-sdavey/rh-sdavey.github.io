---
tags: [vim,sed]

---
#### Change the first word of every line to another word ( in this case up until the first : ) 


[shift] + v    //select code block to change
[shift] + :    //execute control over this block
s/^[^:]\+:/word:/   // subsitute from beginning of line all chars that are not a colon, and then include the colon, with 'word'

##### or using sed

// TODO ADD NEWLINES HERE ( GOOGLE IT ) 



sed -e 's/^[^:]\+:/word:/'   \<filename here\>
  
  
  _____
