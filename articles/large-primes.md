
#  Large Primes: How to check them?
 
---
Question | Answer |
--- | --- |
Writer |  Mayank Khandelwal - MSc I year
Editor | Vipin K Jonwal - MCA II year , Swati Gautam - MSc I year
Status |	Reviewed once. Waiting for checks to be verified. Will review again.
Plagiarism |	None.  100% unique. [Report Link](./plag-reports/plag-large-primes-v1.pdf)
Verdict | Good Candidate. 
Checks Required | 24x7x365 what? , definition of primes could be made more clear, some error/"probability" associated with them?
Checks Reviewed | 24x7x365 hours, analogous to something running for forever. Do we need more naive definition of primes?
---

>“God may not play dice with the universe, but something strange is going on with the prime numbers.”
-Paul Erdos

“December 21, 2018 -- The largest known prime number **2<sup>82589933</sup> - 1** has being discovered by **The Great Internet Mersenne Prime Search (GIMPS)** which has **24,862,048** digits. A computer volunteered by Patrick Laroche from Ocala, Florida made the find on December 7, 2018.”

Primes, whole numbers with two factors, have always influenced the mathematical world with its beauty. It has made cryptography an enigma. Large primes are used in encryption to make networks more secure. And who can forget the million-dollar problem of Riemann Hypothesis, which is based on the distribution of primes? Also, there is a sort of joy in finding large prime numbers in society.

The layman’s way for checking a number to be prime is, trial division of the number n with 2,3 and odd numbers of the form 6k±1 (k>=1) less than or equal to √n. But, the time complexity for executing this is **exponential, (O(2<sub>n/2)</sub>)** to the size of n and is not acceptable for large numbers. Let’s compute for a sample. If we assume, a supercomputer can exexute 1016 iterations in one second and we run this program 24x7x365 hours, it would not have completed till the moment, even if we started at the big-bang to check the primality of largest prime known till date.

The question therefore is, how is the primality of numbers of such huge sizes is checked? 

Methods like Fermat’s Little Theorem and Miller-Rabin test exist, but there is some error/probability associated with them.

Lucas-Lehmer test, developed by Édouard Lucas and improved by him and Derrick Henry Lehmer is used to check the primality of special types of numbers known as Mersenne numbers. These are the numbers of the form 2<sup>n</sup> – 1. Under this test, a Mersenne number, 2<sup>n</sup> -1 is prime, if and only if, n is odd prime and (n-1)th element of the Lucas-Lehmer sequence (given below) is divisible by the number. 

The Lucas-Lehmer sequence is given as –

<pre>L(i) = 4,             i = 1 

L(i) = (L(i-1))^2 – 2,     i > 1</pre>

The sequence grows very fast. First few elements of the sequence are 4, 14, 194, 37634, 1416317954,.…. So, instead of first calculating the (n-1)th element of the sequence and then checking it’s divisibility. We keep on passing just the remainders from ith iteration to (i+1)th, which makes calculation somewhat fast.

Let’s check the primality of 2<sup>7</sup>-1.

2<sup>7</sup>-1 = 127, n = 7

L(1)=4

Incrementing till L(6) by taking remainders from one iteration to next.

<pre>4 mod 127 = 4                                            …L(1)

4<sup>2</sup>-2 mod 127 = 14 mod 127 = 14                     …L(2)

14<sup>2</sup>-2 mod 127 = 194 mod 127 = 67                   …L(3)

67<sup>2</sup>-2 mod 127 = 4487 mod 127 = 42                  …L(4)

42<sup>2</sup>-2 mod 127 = 1762 mod 127 = 111                 …L(5)

111<sup>2</sup>-2 mod 127 = 12319 mod 127 = 0                 …L(6)</pre>

As L(6) mod 127 equals zero. 127 is a prime number.

This is the main idea behind the construction of GIMPS’s algorithm, which is generally used to find large Mersenne primes. GIMPS gives thousands of dollars as prize money for finding large primes to the enthusiasts.

An algorithm for primality checking of all types of numbers is also of theoretical interest known as AKS primality test, founded by IIT Kanpur’s professors named Manindra Agrawal, Neeraj Kayal and Nitin Saxena, in 2002. It is a generalization of Fermat’s Little Theorem polynomial. It states that a number n is prime if all the coefficients of polynomial (x - 1)<sup>n</sup> - (x<sup>n</sup> - 1) are divisible by n. This algorithm runs in polynomial time with the size of n. AKS’s correctness is based on the generalized Riemann Hypothesis. It is not much used in practice as other fast algorithms also exist which works on a particular type of number.

Some amusing facts :

>The largest prime found without using a computer is, (1/17)*(2<sup>148</sup>+1) (a Proth number)by Aime Ferrier. He used a mechanical calculator and Proth’s theorem for this.

>The largest prime checked just by hand calculations is 2<sup>127</sup>-1 by Lucas. Using his Lucas-Lehmer sequence.

>It is difficult (but scientifically possible) to remember all the digits of the largest prime known till date in decimal by humans. But you may remember it in binary ;)



  














 
 
 
 
