Namely, z3py is a framework that allows you to define all sorts of variables ( int's, real numbers, bit vectors, or even functions [f(x)] !), add some constraints that they need to comply with, and it will give you the result.

The easiest example you could think of is an equation system:

```python
x = Int('x')
y = Int('y')
solve(x > 2, y < 10, x + 2*y == 7)
```

Easiest way to install Z3Py on Windows (can be used in Linux as well):
*https://github.com/Z3Prover/z3/wiki/Using-Z3Py-on-Windows

Quick guide with examples to get started:
*http://ericpony.github.io/z3py-tutorial/guide-examples.htm

## Use
This tool can be really valuable for solving CTF challenges. Below, you can see a write-up for [Google´s 2016 "Unbreakable enterprise product activation" CTF challenge](https://github.com/ctfs/write-ups-2016/tree/master/google-ctf-2016/reverse/unbreakable-enterprise-product-activation-150). It is also a great example to learn how to work with bit vectors:
* https://p1kachu.pluggi.fr/writeup/re/2016/05/01/googlectf-unbreakable-writeup/
