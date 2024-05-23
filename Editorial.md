# Editorial: Spike and Faye's Constrained Sum Game

## Problem Analysis

Spike and Faye are playing a game where they start with a number \(N\) and aim to reach exactly \(T\) by subtracting proper divisors of \(N\). The player who cannot make a valid move loses the game.

## Approach

1. **Proper Divisors**
   To determine the proper divisors of \(N\), iterate from 1 to \(\sqrt{N}\). For each integer \(i\) that divides \(N\), both \(i\) and \(\frac{N}{i}\) (if different from \(N\)) are proper divisors.

2. **DP with Memoization**:
   Use memoization to store the results of subproblems. For each state \(N\), store whether Spike or Faye wins if the game starts with \(N\).

3. **Game Simulation**:
   Simulate the game by trying all possible proper divisors. If Spike can make a move that leaves Faye in a losing position, then Spike wins. Otherwise, Faye wins.

4. **Edge Cases**:
   Handle cases where \(T\) is close to \(N\) or where \(N\) has very few divisors.

## Solution

#include <iostream>
#include <vector>
#include <unordered_map>
using namespace std;

// here we have a func. which finds all proper divisors of N


vector<long long> divs(long long N) {
    vector<long long> divisors;
    for (long long i=1; i*i <= N; ++i) {
        if (N%i == 0) {
            if (i != N) divisors.push_back(i);
            if (i != 1 && i != N / i) divisors.push_back(N / i);
        }
    }
    return divisors;
}



string findthewinner(long long N, long long T, unordered_map<long long, string>& memo) {
   
    if (memo.count(N)) {
        return memo[N];
    }

    vector<long long> divisors = divs(N);
    for (long long d : divisors) {
        long long newN = N - d;
        if (newN < T) continue;
        if (newN == T) {
            memo[N] = "Spike";
            return "Spike";
        }
        if (findthewinner(newN, T, memo) == "Faye") {
            memo[N] = "Spike";
            return "Spike";
        }
    }

    memo[N] = "Faye";
    return "Faye";
}




int main() 
{
   
    int t;
   
    cin >> t;

    unordered_map<long long, string> memo;
    memo[1] = "Faye";  // edge case: If N == 1, Faye loses

    while (t--) {
        long long N, T;
        cin >> N >> T;
        cout << findthewinner(N, T, memo) << endl;
    }
}
