Problem




https://buckeyectf-21-7890394b80c62b0a5e499176061926a1d1469003.storage.googleapis.com/uploads/65ee275be3cc67e076e68ab9be64cc7af8f9cea89ab180aa7a053907303cf1c4/server.py




this problem is the advanced version of Write up: Key exchange




the source code indicates:

\(p=\)random prime large number

\(a=\)random (large) number between 2 and \(p\)-1

\(g\) is 5

\(A\equiv g^a \mod p\) [1]

only \(g,p\) will be given,but not \(A\) 

you provide \(1 < B < p-1\)

you need to find the value of shared_secret (ss)

\(ss\equiv B^a \mod p\) [2]




Solution

this time we only could use formula [2], 

recall the Fermat Little Theory

$$a^{p-1} \equiv 1 \mod p$$

we could make some possible \(B \equiv b^{(p-1)/4} \mod p\), and hope \(a\) is multiple of 4 




I chose 4 here, because \( b^{(p-1)/2} \equiv \pm 1 \mod p\),which does not work
