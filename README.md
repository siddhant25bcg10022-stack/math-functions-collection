# math-functions-collection
A collection of simple and well-structured Python functions based on number theory concepts. This project covers factorials, prime checks, divisor functions, modular arithmetic, special number tests, and more — all implemented without using any external libraries. The code is clean, beginner-friendly, and organized for academic use and learning.

# -----------------------------------------
# 1. Factorial of n
# -----------------------------------------
    def factorial(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result


# -----------------------------------------
# 2. Palindrome Check
# -----------------------------------------
    def is_palindrome(n):
    s = str(n)
    return s == s[::-1]


# -----------------------------------------
# 3. Mean of Digits
# -----------------------------------------
    def mean_of_digits(n):
    digits = str(n)
    total = 0
    for d in digits:
        total += int(d)
    return total / len(digits)


# -----------------------------------------
# 4. Digital Root
# -----------------------------------------
    def digital_root(n):
    while n > 9:
        total = 0
        for d in str(n):
            total += int(d)
        n = total
    return n


# -----------------------------------------
# Helper: Sum of Proper Divisors
# -----------------------------------------
    def sum_proper_divisors(n):
    total = 1
    i = 2
    while i * i <= n:
        if n % i == 0:
            total += i
            if i != n // i:
                total += n // i
        i += 1
    return total if n > 1 else 0


# -----------------------------------------
# 5. Abundant Number Check
# -----------------------------------------
    def is_abundant(n):
    return sum_proper_divisors(n) > n


# -----------------------------------------
# 6. Deficient Number Check
# -----------------------------------------
    def is_deficient(n):
    return sum_proper_divisors(n) < n


# -----------------------------------------
# 7. Harshad Number
# -----------------------------------------
    def is_harshad(n):
    s = 0
    for d in str(n):
        s += int(d)
    return n % s == 0


# -----------------------------------------
# 8. Automorphic Number
# -----------------------------------------
    def is_automorphic(n):
    square = n * n
    return str(square).endswith(str(n))


# -----------------------------------------
# 9. Pronic Number
# -----------------------------------------
    def is_pronic(n):
     i = 1
    while i * (i + 1) <= n:
        if i * (i + 1) == n:
            return True
        i += 1
    return False


# -----------------------------------------
# Helper: Prime Check
# -----------------------------------------
    def is_prime(n):
    if n < 2:
        return False
    i = 2
    while i * i <= n:
        if n % i == 0:
            return False
        i += 1
    return True


# -----------------------------------------
# 10. Prime Factors
# -----------------------------------------
    def prime_factors(n):
    factors = []
    i = 2
    while i * i <= n:
        while n % i == 0:
            factors.append(i)
            n //= i
        i += 1
    if n > 1:
        factors.append(n)
    return factors


# -----------------------------------------
# 11. Count Distinct Prime Factors
# -----------------------------------------
    def count_distinct_prime_factors(n):
    factors = prime_factors(n)
    unique = []
    for f in factors:
        if f not in unique:
            unique.append(f)
    return len(unique)


# -----------------------------------------
# 12. Prime Power Check (p^k)
# -----------------------------------------
    def is_prime_power(n):
    if n < 2:
        return False
    p = 2
    while p * p <= n:
        if n % p == 0:
            x = n
            while x % p == 0:
                x //= p
            return x == 1
        p += 1
    return True  # n is prime → p^1


# -----------------------------------------
# 13. Mersenne Prime Check
# -----------------------------------------
    def is_mersenne_prime(p):
    if not is_prime(p):
        return False
    m = (2 ** p) - 1
    return is_prime(m)


# -----------------------------------------
# 14. Twin Primes up to limit
# -----------------------------------------
    def twin_primes(limit):
    twins = []
    for n in range(2, limit + 1):
        if is_prime(n) and is_prime(n + 2):
            twins.append((n, n + 2))
    return twins


# -----------------------------------------
# 15. Number of Divisors d(n)
# -----------------------------------------
    def count_divisors(n):
    count = 0
    i = 1
    while i * i <= n:
        if n % i == 0:
            if i * i == n:
                count += 1
            else:
                count += 2
        i += 1
    return count


# -----------------------------------------
# 16. Aliquot Sum
# -----------------------------------------
    def aliquot_sum(n):
    return sum_proper_divisors(n)


# -----------------------------------------
# 17. Amicable Numbers
# -----------------------------------------
    def are_amicable(a, b):
    return aliquot_sum(a) == b and aliquot_sum(b) == a


# -----------------------------------------
# 18. Multiplicative Persistence
# -----------------------------------------
    def multiplicative_persistence(n):
    steps = 0
    while n > 9:
        product = 1
        for d in str(n):
            product *= int(d)
        n = product
        steps += 1
    return steps


# -----------------------------------------
# 19. Highly Composite Number
# -----------------------------------------
    def is_highly_composite(n):
    d_n = count_divisors(n)
    i = 1
    while i < n:
        if count_divisors(i) >= d_n:
            return False
        i += 1
    return True


# -----------------------------------------
# 20. Modular Exponentiation
# -----------------------------------------
    def mod_exp(base, exp, mod):
    result = 1
    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod
        base = (base * base) % mod
        exp //= 2
    return result


# -----------------------------------------
# 21. Modular Multiplicative Inverse
# -----------------------------------------
    def mod_inverse(a, m):
    a = a % m
    for x in range(1, m):
        if (a * x) % m == 1:
            return x
    return None


# -----------------------------------------
# 22. Chinese Remainder Theorem
# -----------------------------------------
    def crt(remainders, moduli):
    x = 0
    M = 1
    for m in moduli:
        M *= m
    for r, m in zip(remainders, moduli):
        Mi = M // m
        inv = mod_inverse(Mi, m)
        x += r * Mi * inv
    return x % M


# -----------------------------------------
# 23. Quadratic Residue Check
# -----------------------------------------
    def is_quadratic_residue(a, p):
    a = a % p
    for x in range(p):
        if (x * x) % p == a:
            return True
    return False


# -----------------------------------------
# 24. Order Modulo n
# -----------------------------------------
    def order_mod(a, n):
    k = 1
    value = a % n
    while value != 1:
        value = (value * a) % n
        k += 1
    return k


# -----------------------------------------
# 25. Fibonacci Prime Check
# -----------------------------------------
    def is_fibonacci_prime(n):
    if not is_prime(n):
        return False
    a, b = 0, 1
    while b < n:
        a, b = b, a + b
    return b == n


# -----------------------------------------
# 26. Lucas Sequence
# -----------------------------------------
    def lucas_sequence(n):
    seq = []
    a, b = 2, 1
    for _ in range(n):
        seq.append(a)
        a, b = b, a + b
    return seq


# -----------------------------------------
# 27. Perfect Power Check
# -----------------------------------------
    def is_perfect_power(n):
       if n <= 3:
          return False
        for a in range(2, n):
          x = n
           while x % a == 0:
            x //= a
        if x == 1:
            return True
    return False


# -----------------------------------------
# 28. Collatz Sequence Length
# -----------------------------------------
    def collatz_length(n):
      steps = 0
         while n != 1:
          if n % 2 == 0:
              n //= 2
          else:
              n = 3 * n + 1
            steps += 1
          return steps


# -----------------------------------------
# 29. Polygonal Number
# -----------------------------------------
    def polygonal_number(s, n):
         return ((s - 2) * n * n - (s - 4) * n) // 2


# -----------------------------------------
# 30. Carmichael Number Check
# -----------------------------------------
    def is_carmichael(n):
      if is_prime(n):
        return False
    a = 2
    while a < n:
        if gcd(a, n) == 1:
            if mod_exp(a, n - 1, n) != 1:
                return False
        a += 1
    return True


# -----------------------------------------
# Helper: GCD
# -----------------------------------------
    def gcd(a, b):
       while b != 0:
        a, b = b, a % b
    return a


# -----------------------------------------
# 31. Miller-Rabin Primality Test
# -----------------------------------------
    def is_prime_miller_rabin(n, k):
    if n < 2:
       return False
     if n % 2 == 0:
       return n == 2

    d = n - 1
    r = 0
    while d % 2 == 0:
        d //= 2
        r += 1

    def test(a):
        x = mod_exp(a, d, n)
        if x == 1 or x == n - 1:
            return True
        for _ in range(r - 1):
            x = (x * x) % n
            if x == n - 1:
                return True
        return False

    base = 2
    for _ in range(k):
        if not test(base):
            return False
        base += 1

    return True


# -----------------------------------------
# 32. Pollard Rho Factorization
# -----------------------------------------
    def pollard_rho(n):
    if n % 2 == 0:
        return 2

    def f(x):
        return (x * x + 1) % n

    x, y = 2, 2
    d = 1

    while d == 1:
        x = f(x)
        y = f(f(y))
        d = gcd(abs(x - y), n)

    return d if d != n else None


# -----------------------------------------
# 33. Zeta Approximation
# -----------------------------------------
    def zeta_approx(s, terms):
      total = 0.0
    for n in range(1, terms + 1):
        total += 1 / (n ** s)
    return total


# -----------------------------------------
# 34. Partition Function (simple recursion)
# -----------------------------------------
    def partition_function(n):
    if n == 0:
        return 1
    total = 0
    for i in range(1, n + 1):
        total += partition_function(n - i)
    return total
