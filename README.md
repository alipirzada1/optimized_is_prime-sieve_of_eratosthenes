# optimized_is_prime-sieve_of_eratosthenes
A simple optimized version of to calculate Prime numbers using optimize_is_prime and Sieve of Eratosthenes

# optimized_is_prime
is_prime is somewhat slow for large numbers. This is because we are doing a ton of extra work checking every possible factor of the tested number. We will use two optimizations to make a get_primes_fast_optimized function.

First optimization takes advantage of the fact that two is the only even prime. Thus we can check if a number is even and as long as its greater than 2, we know that it is not prime.

Second optimization takes advantage of the fact that when checking factors, we only need to check odd factors up to the square root of a number. Consider a number  n  decomposed into factors  n=ab. There are two cases, either  n  is prime and without loss of generality,  a=n,b=1  or n is not prime and  a,b≠n,1 . In this case, if  a>√n , then  b<√n . So we only need to check all possible values of  b and we get the values of  a. This means that even the simple method of checking factors will increase in complexity as a square root compared to the size of the number instead of linearly.

# sieve_of_eratosthenes

An even faster method for calculating prime numbers which is known as the Sieve of Eratosthenes (although it is more expensive in terms of memory). The Sieve of Eratosthenes is an example of dynamic programming, where the general idea is to not redo computations we have already done. We will break this sieve down into several small functions.

The method works as follows
1. Generate a list of all numbers between 0 and N; mark the numbers 0 and 1 to be not prime
2. Starting with  p=2  (the first prime) mark all numbers of the form  np  where  n>1  and  np<=N  to be not prime (they can't be prime      since they are multiples of 2!)
3. Find the smallest number greater than  p  which is not marked and set that equal to  p , then go back to step 2. Stop if there is no      unmarked number greater than  p  and less than  N+1

We will break this up into a few functions
1. `list_true` Make a list of true values of length  n+1  where the first two values are false (this corresponds with step 1 of the           algorithm above)
2. `mark_false` takes a list of booleans and a number  p . Mark all elements  2p,3p,...n  false (this corresponds with step 2 of the           algorithm above)
3. `find_next` Find the smallest `True` element in a list which is greater than some  p  (has index greater than p (this corresponds with     step 3 of the algorithm above)
4. `prime_from_list` Return indices of True values
