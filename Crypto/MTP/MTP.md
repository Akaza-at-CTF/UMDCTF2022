# MTP

> One-time pad? More like multiple-time pad ;)
> 
> NOTE: You can assume that the plaintexts are grammatically-correct English sentences
> 
> FLAG FORMAT: Concatenate all 8 plaintext sentences together like so: "[pt1][pt2][pt3][pt4][pt5][pt6][pt7][pt8]" and take the MD5 hash of this string. Wrap the MD5 hash in the flag format to submit.
> 
> ```python
> import hashlib
> plaintexts = [...]
> 
> pt_str = ''
> for pt in plaintexts:
>     pt_str += pt
> 
> print('UMDCTF{' + hashlib.md5(pt_str.encode()).hexdigest() + '}')
> ```
> 
> Author: itsecgary

The encryption only uses XOR so we can use [dcode](https://www.dcode.fr/xor-cipher) to find the key given it is of length 30. The bruteforce attempt isn't perfect, but it works considerably well as we now have mostly Enlgish words. From the assumption, we can also guess the first letter of the first word (it will be uppercase) and the last character of a sentence should be a period (or some other punctuation mark). After a bit of trial and error, the key is `8a619ee676527b384a9fd54f505bab0bbecc96316d2c4fc49a3dbc5af2d5`. Use the template to find the hash value.

The flag is `UMDCTF{0a46e0b2b19dc21b5c15435653ffed67}`.
