# CP_template
Competitive Coding Template
<br>

// I am using c++ gcc 11.2.0       
// X % 2^k ===> X & ((1<<k)-1)

// swapping two variables ( X and Y)
// step 1 : X = X ^ Y       
// step 2 : Y = X ^ Y
// step 3 : X = X ^ Y

// small alphabet mai 5th bit set hota hai 
// Capital alphabet mai 5th bit unset hota hai
// A = 65 <--> Z = 90 , a = 97 , z = 122 
// subtract 32 from lower case to get upper case
/*--------------------Property------------

No. of set bits in A  = X 
No. of set bits in B = Y
No. of set bits in (A^B) = Z

then Z is even if X+Y  is even
     Z is odd if X+Y is odd
*/   

//if X = 10 then make it X = 5 and vice versa ==> X = 10^5^X
//if we take & of more number it leads to minimum number.

// a<<b ===> a*(2^b)
// a>>b ===> a/(2^b)   
// if 8 = 001000 then ~8 = 110111 ( toggle all the bits if we take NOT)      
// int n = max({a,b,c});  === > max of three elements        
// to stop the process : net stop http | (taskkill -im File.exe -f)       
// oops size(x), rbegin(x), rend(x) need C++17        
// Name : kamlesh kaparvena 


//#include <bits/stdc++.h>
#include <cstdio>
#include <iostream>
#include <vector>
#include <algorithm>
#include <string>
#include <ctype.h>
#include <queue>
#include <cstring>  //memset
#include <set>
#include <bitset>
#include <map>
#include <chrono>
#include <random>
#include <unordered_map>
#include <stdio.h>
#include <cassert>
#include <climits>
#include <cmath>
#include <complex>
#include <functional>
#include <iomanip>
#include <array>
#include <numeric>    //iota

using namespace std;


//_______________________________________define______________________________________________

#define ll long long 
#define f float
#define endl "\n"
#define For(i,n) for(int i=0;i<(int)n;i++)
#define Rev(i,n) for(int i=n-1;i>=0;i--)
#define tern(a,b,c) (!!(a))*b+(!(a))*c
#define cross(i,a,b) ((tern(b>a,1,-1))*(i))>=((tern(b>a,1,-1))*(b))
#define loop(i,a,b) for(int i=a;i!=b;i+=tern(b>a,1,-1))
#define sloop(i,a,b,s) for(int i=a;(!(cross(i,a,b)));i+=s)
#define inrange(i,a,b) ((i>=min(a,b)) && (i<=max(a,b)))
#define F first
#define S second
#define pb push_back
#define mp make_pair
#define d0(x) cout<<(x)<<" "
#define d1(x) cout<<(x)<<endl
#define d2(x,y) cout<<(x)<<" "<<(y)<<endl
#define d3(x,y,z) cout<<(x)<<" "<<(y)<<" "<<(z)<<endl
#define d4(a,b,c,d) cout<<(a)<<" "<<(b)<<" "<<(c)<<" "<<(d)<<endl
#define d5(a,b,c,d,e) cout<<(a)<<" "<<(b)<<" "<<(c)<<" "<<(d)<<" "<<(e)<<endl
#define d6(a,b,c,d,e,f) cout<<(a)<<" "<<(b)<<" "<<(c)<<" "<<(d)<<" "<<(e)<<" "<<(f)<<endl
#define speed ios_base::sync_with_stdio(false);cin.tie(NULL);
#define ordered_set tree<int, null_type,less<int>, rb_tree_tag,tree_order_statistics_node_update>
#define MS0(X) memset((X), 0, sizeof((X)))
#define MS1(X) memset((X), -1, sizeof((X)))
#define read(x) scanf("%d", &x)
#define take(x,y,z) scanf("%d%d%d",&x,&y,&z)
#define debug(x) for(auto I : x){cout<<I<<" ";}
#define lb lower_bound
#define up upper_bound

//_________________________________________values_____________________________________

const int maxn=1e6+100;
const int MaxN=1e5+100;
const int mod=1e9+7;
const double PI=3.14159265358979323846264338327950288419716939937510582097494459230;
const int dx[4]{1, 0, -1, 0}, dy[4]{0, 1, 0, -1};  // for every grid problem!!

//______________________________functions______________________________________________

inline int fast_expo(int base,int power,int modulo=mod){
    base%=mod;
    if (base<0) base+=mod;
    ll x=base,cnt=power,ans=1;
    while(cnt){
        if (cnt&1) ans=(ans*x)%mod;
        x=(x*x)%mod;
        cnt>>=1;
    }
    // int tmp=ans;
    return ans;
}

inline int fib(int n,int a=1,int b=1,int c=1,int d=0,int acca=0,int accb=1,int m=mod){
    if (n==0){ 
    return acca;
    }
    if (n&1){
    return fib(n/2,((a*a)%m+(b*c)%m)%m,((a*b)%m+(b*d)%m)%m,(c*(a+d)%m)%m,((c*b)%m+(d*d)%m)%m,((a*acca)%m+(b*accb)%m)%m,((c*acca)%m+(d*accb)%m)%m,m);
    }
    else{
    return fib(n/2,((a*a)%m+(b*c)%m)%m,((a*b)%m+(b*d)%m)%m,(c*(a+d)%m)%m,((c*b)%m+(d*d)%m)%m,acca,accb,m);
    }
}

ll gcd (ll a, ll b) {return b==0 ? a : gcd(b, a%b);}

bool ispowerof2(int n){
    if(n == 0){
      return false;
    }
    else{
      if(n & (n-1)){      // zero it is power of 2 otherwise not
        return false;
      }
      else{
        return true;
      }
    }
}
int settheKthbit(int n,int k){
    return (n | (1<<k));
}
int unsettheKthbit(int n,int k){
    return (n | ~(1<<k));
}
bool isKthbitset(int k,int n){
    if(n & (1<<k)){
      return true;
    }
    else{
      return false;
    }
}
int togglethekthbit(int n,int k){
    return (n^(1<<k));
}
int numberofsetbit(int n){   // does in O(1)
    return __builtin_popcount(n);
}
ll numberofsetbitlong(ll n){   // does in O(1)
    return __builtin_popcountll(n);
}
bool isodd(int n){
  if(n == 0){
    return false;
  }else{
    if(n&1){
       return true;
    }
    else{
       return false;
    }
  }
}

int noofdigits(int n){
    return (floor(log10(n) + 1));
}



//_________________________________________Matrix_exponentiation________________________________

void Miden(ll **pl,ll n){
  ll (*x)[n] = (ll(*)[n]) pl;
  for(int i=0;i<n;i++){
         for(int j=0;j<n;j++){
            x[i][j] = 0;
         }
         x[i][i] = 1; 
  }
  return ;
}

void Mmult(ll **p1,ll **p2,ll **ans,ll x,ll y,ll z,ll m)
{
   ll (*a)[y] = (ll (*)[y])p1;
   ll (*b)[z] = (ll (*)[z])p2;
   ll (*c)[z] = (ll (*)[z])ans;

   for(int i=0;i<x;i++){
     for(int j=0;j<z;j++)
     {
      c[i][j] = 0;
      for(int k=0;k<y;k++){
        c[i][j] += a[i][k]*b[k][j];
        c[i][j]%=m;
      }
     }
   }
   return;
}


 void Mpow(ll **p1,ll **ans,ll n,ll y,ll m)
{
   if(y  == 0){         // base case
     Miden(ans,n);    // this is the identity case
     return ;
   }
   ll t[n][n];
   Mpow(p1,(ll **)t,n,y/2,m);
   ll z[n][n];
   Mmult((ll **)t,(ll **)t,(ll **)z,n,n,n,m);
   if(y%2){
    Mmult((ll **)z,p1,ans,n,n,n,m);
   }
   else{
    Miden((ll **)t,n);
    Mmult((ll **)z,(ll **)t,ans,n,n,n,m);
   }
   return;
}

/* int main()
{
  int n;
  cin>>n;

  ll mat[2][2] = {
    {1,1},
    {1,0}
  };

  ll ans[2][2];
  // data type of ans is (ll (*)[2])

  Mpow((ll **)mat,(ll **)ans,2,n-1,1000000007);

  // cout<<(ans[0][1] ) % 1000000007;
  cout<<(ans[0][0]) % mod; 
 return 0;
} */

//_________________________________________Policy Based Datastructure____________________________________________

// find_by_order(k)  returns iterator to kth element starting from 0;
// order_of_key(k) returns count of elements strictly smaller than k;


//_______________________________________Code start here__________________________________________________
// Don't go for one approach  
// think reverse
// Read the Question properly (IMPORTANT)
void solve(){
     
     

}


int main()
{
  int T; 
  read(T);
  while(T--)
  {
    solve();

  }
 return 0;
}
//______________________________________otherstuff____________________________________________________
/*
void test_cases(){
    
}

int main(){
    int T; scanf("%d",&T);
    for(int z=1;z<=T;z++){
    printf("Case #%d: ",z);
    test_cases();
    }
}
*/

//____________________________________complexity____________________________________________

//sort ==> O((N)logN)
//



//_____________________________________________STL_________________________

//stl has 4 components
//1. algorithms
//2. Containers
//3. Functors
//4. iterators






//____________________________________Diagram______________________________


                  

                                                                     
        //              /--------\                      |-------------|          |-----------|
        //             / is order \                     |Last IN      |          |first in   |
        //            /  important \                    |First OUt    |          |first out  |----no---) 
        //           /      ?       \------YES----------|             |----NO----|           |         |
        //           \              /                   --------------|          |-----------|         |
        //            \____________/                           |                         |            priority_queue   
        //                   |                                 |                         |        
        //                   |                                 |                        YES 
        //                   NO                                YES                       |
        //                   |                                 |                         |
        //             allow duplicates                        |                         | 
        //                 /       \                        ------------               queue
        //                /         \                      |           |
        //               /           \                     |  Stack    |       
        //              NO            \                    |           |
        //             /               \                   ------------
        //            /                 \ 
        //       map key to value        \
        //          /\                    Yes---------------) 
        //         /  \                                     |
        //        /    \                                 map key to value
        //       /      \                                   /        \
        //      /        \                                 /          \ 
        //     yes        \                               /            \
        //     /           \                             yes            \
        //    /             NO                           /               NO
        // unordered_map     \                          /                 \
        //                    \                        /                  unordered_multiset
        //                    unordered_set       unordered_multimap



//____________________________complexity order _______________________________________

//O(1) == kam time lagega
//O(logN)
//O(N)
//O(NlogN)
//O(N^2)
//O(N^3)
//O(2^N)
//O(N!)

//______________________________________otherstuff________________________________________

//reverse(vec2.begin()+3,vec2.begin()+5) ===> this will reverse elements from index 3 to 4
//reverse(vec2.begin(),vec2.end()) ==> this will reverse from beginning to end

//_____________________________________templates_____________________________________
//bstnode
//dsu
//fenwick
//fenwick2d
//linkcut
//pbds
//segtree
//segtreenew
//sparetable
//splay
//treap
//matrixexpo
