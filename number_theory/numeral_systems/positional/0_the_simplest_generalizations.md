### The simplest generalizations      
   
*Change as little as possible* from ordinary decimal positional notation.   
   
Decimal has two core ingredients:   
   
1. a **base** (b=10) (place values (10^k)), and   
2. a **digit set** (D={0,1,\dots,9}) (so each “digit” fits in one place).   
   
So the “simplest generalization” is: keep the *same positional idea*, but let   
   
* (b) be any **integer (>1)**, and   
* digits be exactly (0,1,\dots,b-1).   
   
That preserves the most familiar properties: every integer has a finite expansion, conversion algorithms work cleanly, and (almost) uniqueness holds.   
   
---   
   
## b=0   
   
A positional system with the usual meaning   
```math   
\sum a_k b^k   
```   
basically breaks:   
   
* For (k\ge1), (0^k=0), so higher places contribute nothing.   
* For (k<0), (0^k) would require dividing by 0 (undefined).   
* Even (0^0) is a special case.   
   
So **“base 0” isn’t a workable positional numeral system** in the normal sense.   
   
---   
   
## b=1     
   
That’s the **unary** (tally-mark) system: represent (n) by repeating a symbol (n) times. It exists, but it’s not positional in the usual way (place value doesn’t change). ([Wikipedia][1])   
   
---   
   
## b is negative     
   
Yes — **negative bases are a real thing** and studied.   
   
Example: **base (-2)** (“negabinary”) uses digits ({0,1}) but place values alternate sign:   
```math   
\sum a_k(-2)^k.   
```    
Every integer can be represented **without a minus sign** (at the cost of trickier arithmetic). ([Wikipedia][2])   
   
There’s also a broader theory of “β-expansions” (negative real bases), studied for (β>1). ([EuDML][3])   
   
---   
   
## b is a non-integer   
   
**Non-integer bases** are studied under **β-expansions**.   
   
For any real (β>1), numbers can be represented using digits from a finite set (often ({0,1,\dots,\lfloor\beta\rfloor})) with an algorithmic “greedy” expansion. This was introduced by Rényi (1957) and developed by Parry (1960). ([Webspace][4])   
   
These expansions can be non-unique more often than in integer bases, and many rationals won’t have terminating forms.   
   
---   
   
## Complex bases     
   
Knuth proposed the **quater-imaginary base (2i)**, where every complex number can be represented using digits ({0,1,2,3}). ([Wikipedia][5])   
   
---   
[1]: https://en.wikipedia.org/wiki/Unary_numeral_system?utm_source=chatgpt.com "Unary numeral system"   
[2]: https://en.wikipedia.org/wiki/Negative_base?utm_source=chatgpt.com "Negative base"   
[3]: https://eudml.org/doc/117734?utm_source=chatgpt.com "Beta-expansions with negative bases."   
[4]: https://webspace.maths.qmul.ac.uk/f.vivaldi/teaching/ETAD/NotesII.pdf?utm_source=chatgpt.com "expansions in non-integer bases"   
[5]: https://en.wikipedia.org/wiki/Quater-imaginary_base?utm_source=chatgpt.com "Quater-imaginary base"   
   
