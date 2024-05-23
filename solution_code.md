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

int main() {
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
