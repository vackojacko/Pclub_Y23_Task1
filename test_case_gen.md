#include "testlib.h"
#include <iostream>

using namespace std;

int main(int argc, char* argv[]) {
    registerGen(argc, argv, 1);
    
    int t = rnd.next(1, 100);
    cout << t << endl;
    
    for (int i = 0; i < t; ++i) {
        long long N = rnd.next(3, 1000000000);
        long long T = rnd.next(2, N - 1);
        cout << N << " " << T << endl;
    }

    return 0;
}
