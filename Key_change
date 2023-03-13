Problem




https://buckeyectf-21-7890394b80c62b0a5e499176061926a1d1469003.storage.googleapis.com/uploads/790c4faa91bff603ff4ff4346d83658efd6da50ff83fad8692b88e1a58595650/server.py

the source code indicates:

\(p=\)random prime large number

\(a=\)random (large) number between 2 and \(p\)-1

\(g\) is 5

\(A\equiv g^a \mod p\) [1]

\(g,p\) and  \(A\) will be given

you provide \(1 < B < p-1\)

you need to find the value of shared_secret (ss)

\(ss\equiv B^a \mod p\) [2]




Solution

if we multiple [1] and [2], we get:

\(A*ss\equiv (g*B)^a \mod p\) 




if we select \(B\equiv g^{-1}\) , then \(ss\equiv A^{-1}\) 
