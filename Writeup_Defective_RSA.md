* Problem

https://buckeyectf-21-7890394b80c62b0a5e499176061926a1d1469003.storage.googleapis.com/uploads/17dfa175fc42810c163f411ee43972e408d02f9b2d842b0d33aef93123a8a8f7/chall.py

4 numbers were give

`e` is the encryption key
`p` and `q` are two primes
`c` is the encrypted number

it implies:

assume `T` is the original clear text, we have `T^{e} \equiv c \mod (p*q)`




As the title says, it is a RSA-like encryption. but e is not co-prime with \(\phi=LCD(p-1,q-1)\) , otherwise, that is the RSA case, d is very easy to calculate: 

\[ d*e \equiv 1 ( \mod \phi)  \] 




Solution

first we realize that \(g=gcd(\phi,e)>1\)

step 1: find \(d\)

if  we could calculate the \(d\) which \(d*e \equiv 1 (\mod \frac{\phi}{g}) \) 

we would have [1]:

$$c^d \equiv T^{e*d} \equiv T^{\frac{\phi*k}{g}+1} \equiv T*T^{\frac{\phi*k}{g}} \mod (p*q)     $$

now we want know this value !!:

$$X = T^{\frac{\phi*k}{g}}  \mod (p*q)$$




step 2: find \(Y\) and \(Z\)

fortunately we know \(X^g \equiv T^{\phi*k} \equiv 1 \mod (p*q)\), so now the problem is to find:

$$X^g \equiv 1 \mod (p*q)$$




we could find \(Y\) and \(Z\) first and then use CRT (Chinese Remainder Theory) to get \(x\) 

$$Y^g \equiv 1 \mod (p)$$

$$Z^g \equiv 1 \mod (q)$$




Assume we have \(g1=\gcd(g,p)\), and \(b\) is a primative root of \(p\),

$$Y=b^{\frac{p-1}{g1}}$$

it is easy to prove \(Y^g \equiv 1 \mod (p)\) by using FLT (Fermat Little Theory) 

we notice because b is the primitive root, all the value of \(Y^i\) also works

for \(i\) in {0,1,2,...g1-1} 

$$(Y^i)^g \equiv 1 \mod (p)$$

similarly we could get a list of Z values

step 3: find \(X\) 

so now we have a list of Y values and a list of Z values. we need to combine them using CRT

recall

$$X=Z*p^{-1}*p+Y*q^{-1}*q  \mod (p*q)$$

Final step : find \(T\) 

now we got a list of X values

try to put them back to [1]

$$T\equiv c^d* X^{-1} \mod (p*q)$$




there will be a list of them but only one would look like a valid flag

by the way, for our problem:

e=1440
g=10
g1=10
g2=2

so we have max 20 of X values

I used  \(b\) =2 

QED




ref:

https://crypto.stackexchange.com/questions/81949/how-to-compute-m-value-from-rsa-if-phin-is-not-relative-prime-with-the-e

https://math.stackexchange.com/questions/158344/how-to-find-the-solutions-for-the-n-th-root-of-unity-in-modular-arithmetic

https://github.com/HackThisSite/CTF-Writeups/blob/master/2017/EasyCTF/RSA%204/README.md ( didn't find it during the contest somehow )

https://en.wikipedia.org/wiki/RSA_(cryptosystem)
