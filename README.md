## 0/1 Knapsack (Recursion and memoization)

> it's an example, a theif entered the house , he decided to take the most valuable things becuase he has a limited storage in his bag so you have two arrays one for the weoght and other for the value also the bag capacity.
 
![Screenshot_3](https://user-images.githubusercontent.com/60802724/200031172-2a596480-3d14-4950-b87d-b38f85b2f6ae.png)

> we will use memoziation to optimize the time by saving the maximum of the route for every index and remainder of the capacity in the bag.
```
#include <iostream>
#include <bits/stdc++.h>
#define ll long long
#define Fast ios_base::sync_with_stdio(false);cout.tie(NULL);cin.tie(NULL);
#define clr(x) memset(x, -1, sizeof(x));

using namespace std;
int numList[] = {5, 2, 7, 3, 4, 6};

ll memo[5][13];

int LIS(int i,int prev){

      if(i == 6 ) return 0;
      ll &ret = memo[i][prev];
      if(memo[i][prev] != -1) return ret;
      int con1 = LIS(i+1,prev);
      int con2 = 0 ;
      if(numList[i] >= numList[prev] )
       con2 = LIS(i+1, i) + 1;

      return ret = max(con1,con2);
}
bool sortbysec(const pair<ll,ll> &a,
              const pair<ll,ll> &b)
{
    return (a.second > b.second);
}

const int MAX = 5;
int w[MAX] = {10,4,20,5,7};
int v[MAX] = {10,15,3,1,4};
int z = 12;

ll knapsack(ll i , ll reminder){
      if(i == 5) return 0;
      if(memo[i][reminder] != -1) return memo[i][reminder];
      ll ch1 = knapsack(i +1, reminder);
      ll ch2 = 0;
      if(reminder - w[i]  >= 0) ch2 = knapsack(i+1, reminder - w[i]) + v[i];
      return memo[i][reminder] = max(ch1,ch2);
}
int main() {
    // Fast;
    clr(memo);
    cout << knapsack(0,12);
}

```
<!---
SORVER/SORVER is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
