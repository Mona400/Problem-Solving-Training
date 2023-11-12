<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="80" src="/logos/hackerrank.png"></img></a>

# HackerRank OJ - Algorithms Basics <br> Math Fundamentals I `15 problems`

## Find the Point
Problem Link: https://hackerrank.com/challenges/find-point/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def findPoint(px, py, qx, qy):
    return (qx + (qx - px)), (qy + (qy - py))
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
vector<int> findPoint(int px, int py, int qx, int qy) {
    return {qx + (qx - px), qy + (qy - py)};
}
```

</details>
<br>

## Maximum Draws
Problem Link: https://hackerrank.com/challenges/maximum-draws/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def maximumDraws(n):
    return n + 1
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int maximumDraws(int n) {
    return n + 1;
}
```

</details>
<br>

## Handshake
Problem Link: https://hackerrank.com/challenges/handshake/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def handshake(n):
    return n * (n - 1) // 2
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int handshake(int n) {
    return n * (n - 1) / 2;
}
```

</details>
<br>

## Minimum Height Triangle
Problem Link: https://hackerrank.com/challenges/lowest-triangle/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def lowestTriangle(base, area):
    return (2 * area + base - 1) // base
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int lowestTriangle(int base, int area) {
    return (2 * area + base - 1) / base;
}
```

</details>
<br>

## Army Game
Problem Link: https://hackerrank.com/challenges/game-with-cells/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def gameWithCells(n, m):
    return ((n+1)//2) * ((m+1)//2)
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int gameWithCells(int n, int m) {
    return ((n+1)/2) * ((m+1)/2);
}
```

</details>
<br>

## Leonardo's Prime Factors
Problem Link: https://hackerrank.com/challenges/leonardo-and-prime/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def primeCount(n):
    primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
    cnt, res = 0, 1
    for j in primes:
        res *= j
        if res <= n:
            cnt += 1
    return cnt
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int primeCount(long n) {
    vector<int> primes = {2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47};
    long cnt = 0, res = 1;
    for (auto &j : primes) {
        res *= j;
        if (res <= n)
            cnt ++;
    }
    return cnt;
}
```

</details>
<br>

## Connecting Towns
Problem Link: https://hackerrank.com/challenges/connecting-towns/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def connectingTowns(n, routes):
    res = 1
    for i in routes:
        res = (res * i) % 1234567
    return res
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int connectingTowns(int n, vector<int> &routes) {
    int res = 1;
    for (auto &i : routes)
        res = (res * i) % 1234567;
    return res;
}
```

</details>
<br>

## Cutting Paper Squares
Problem Link: https://hackerrank.com/challenges/p1-paper-cutting/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def solve(n, m):
    return n * m - 1
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
long solve(int n, int m) {
    return 1LL * n * m - 1;
}
```

</details>
<br>

## Sherlock and Moving Tiles
Problem Link: https://hackerrank.com/challenges/sherlock-and-moving-tiles/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
#TODO
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
//TODO
```

</details>
<br>

## Best Divisor
Problem Link: https://hackerrank.com/challenges/best-divisor/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def divisors(n):
    divs = []
    for i in range(1, int(n**.5)+1):
        if n % i == 0:
            divs.append(i)
            divs.append(n // i)
    divs.sort()
    res, max_sum = 0, 0
    for d in divs:
        total = 0
        t = d
        while t:
            total += t % 10
            t //= 10
        if max_sum < total:
            max_sum = total
            res = d
    return res
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int divisors(int n) {
    vector<int> divs;
    for (int i=1; i<sqrt(n)+1; i++) {
        if (n % i == 0) {
            divs.push_back(i);
            divs.push_back(n / i);
        }
    }
    sort(divs.begin(), divs.end());
    int res = 0, max_sum = 0;
    for (auto &d : divs) {
        int total = 0;
        int t = d;
        while (t) {
            total += t % 10;
            t /= 10;
        }
        if (max_sum < total) {
            max_sum = total;
            res = d;
        }
    }
    return res;
}
```

</details>
<br>

## Restaurant
Problem Link: https://hackerrank.com/challenges/restaurant/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def restaurant(l, b):
    d = math.gcd(l, b)
    return (l // d) * (b // d)
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
int restaurant(int l, int b) {
    int d = gcd(l, b);
    return (l / d) * (b / d);
}
```

</details>
<br>

## Reverse Game
Problem Link: https://hackerrank.com/challenges/reverse-game/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
#TODO
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
//TODO
```

</details>
<br>

## Strange Grid Again
Problem Link: https://hackerrank.com/challenges/strange-grid/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
#TODO
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
//TODO
```

</details>
<br>

## Constructing a Number
Problem Link: https://hackerrank.com/challenges/constructing-a-number/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def canConstruct(a):
    if sum(a) % 3 == 0:
        return "Yes"
    else:
        return "No"
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
string canConstruct(vector<int> &a) {
    long arr_sum = accumulate(a.begin(), a.end(), 0LL);
    if (arr_sum % 3 == 0)
        return "Yes";
    else
        return "No";
}
```

</details>
<br>

## Sherlock and GCD
Problem Link: https://hackerrank.com/challenges/sherlock-and-gcd/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
def solve(a):
    curr_gcd = a[0]
    for i in a:
        curr_gcd = math.gcd(curr_gcd, i)
        if curr_gcd == 1:
            return "YES"
    return "NO"
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
string solve(vector<int> &a) {
    int curr_gcd = a[0];
    for (auto &i : a) {
        curr_gcd = gcd(curr_gcd, i);
        if (curr_gcd == 1)
            return "YES";
    }
    return "NO";
}
```

</details>
<br>

## Primitive Problem
Problem Link: https://hackerrank.com/challenges/primitive-problem/problem

<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/python.png"></img></a>
<details>
    <summary>Python Solution</summary>

```python
#TODO
```

</details>
<br>
<a href="/level-2/hackerrank/algorithms-basics/solutions/math-fundamentals-I.md"><img align="right" width="50" src="https://github.com/cs-MohamedAyman/cs-MohamedAyman/blob/master/repos-logos/cpp.png"></img></a>
<details>
    <summary>CPP Solution</summary>

```cpp
//TODO
```

</details>
<br>
