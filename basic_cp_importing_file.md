    #include<bits/stdc++.h>
    #define mod 1000000007
    #define pb push_back
    #define pf push_front
    #define ins insert
    #define mp make_pair
    #define bitcount __builtin_popcount
    #define all(v) v.begin(),v.end()
    #define mem(n,m) memset(n,m,sizeof(n))
    #define pii pair<int,int>
    #define pll pair<long long,long long>
    #define sii set<int>
    #define sll set<long long>
    #define vii vector<int> 
    #define vll vector<long long>
    #define mii map<int,int>
    #define mll map<long long, long long>
    #define lob lower_bound
    #define upb upper_bound
    #define EPSILON 1e-9
    #define PI 3.1415926535897932384626433832795028841971693993751
    typedef long long  ll;
    typedef long double  ldo;
    typedef double  db ;
     
    using namespace std;
     
    using std::string;
     
    static struct IO {
    	char tmp[1 << 10];
    	char cur;
    	inline char nextChar() { return cur = getc_unlocked(stdin); }
    	inline char peekChar() { return cur; }
     
    	inline operator bool() { return peekChar(); }
    	inline static bool isBlank(char c) { return (c < '-' && c); }
    	inline bool skipBlanks() { while (isBlank(nextChar())); return peekChar() != 0; }
     
    	inline IO& operator >> (char & c) { c = nextChar(); return *this; }
     
    	inline IO& operator >> (char * buf) {
    		if (skipBlanks()) {
    			if (peekChar()) {
    				*(buf++) = peekChar();
    				while (!isBlank(nextChar())) *(buf++) = peekChar();
    			} *(buf++) = 0; } return *this; }
     
    	inline IO& operator >> (string & s) {
    		if (skipBlanks()) {	s.clear(); s += peekChar();
    			while (!isBlank(nextChar())) s += peekChar(); }
    		return *this; }
     
    	inline IO& operator >> (double & d) { if ((*this) >> tmp) sscanf(tmp, "%lf", &d); return *this;	}
     
    #define defineInFor(intType) \
    	inline IO& operator >>(intType & n) { \
    		if (skipBlanks()) { \
    			int sign = +1; \
    			if (peekChar() == '-') { \
    				sign = -1; \
    				n = nextChar() - '0'; \
    			} else \
    				n = peekChar() - '0'; \
    			while (!isBlank(nextChar())) { \
    				n += n + (n << 3) + peekChar() - 48; \
    			} \
    			n *= sign; \
    		} \
    		return *this; \
    	}
     
    defineInFor(int)
    defineInFor(unsigned int)
    defineInFor(long long)
     
    	inline void putChar(char c) { putc_unlocked(c, stdout); }
    	inline IO& operator << (char c) { putChar(c); return *this; }
    	inline IO& operator << (const char * s) { while (*s) putChar(*s++); return *this; }
     
    	inline IO& operator << (const string & s) { for (int i = 0; i < (int)s.size(); ++i) putChar(s[i]); return *this; }
     
    	char * toString(double d) { sprintf(tmp, "%lf%c", d, '\0'); return tmp; }
    	inline IO& operator << (double d) { return (*this) << toString(d); }
     
     
    #define defineOutFor(intType) \
    	inline char * toString(intType n) { \
    		char * p = (tmp + 30); \
    		if (n) { \
    			bool isNeg = 0; \
    			if (n < 0) isNeg = 1, n = -n; \
    			while (n) \
    				*--p = (n % 10) + '0', n /= 10; \
    			if (isNeg) *--p = '-'; \
    		} else *--p = '0'; \
    		return p; \
    	} \
    	inline IO& operator << (intType n) { return (*this) << toString(n); }
     
    defineOutFor(int)
    defineOutFor(long long)
     
    #define endl ('\n')
    #define cout __io__
    #define cin __io__
    } __io__;
     
    std::ostream&
    operator<<(std::ostream & dest, __int128_t value){
        std::ostream::sentry s(dest);
        if(s){
            __uint128_t tmp=value<0?-value:value;
            char buffer[128];
            char* d=std::end(buffer);
            do{
                --d;
                *d="0123456789"[tmp%10];
                tmp/=10;
            }while(tmp!=0);
            if(value<0){
                --d;
                *d='-';
            }
            int len=std::end(buffer)-d;
            if(dest.rdbuf()->sputn(d,len)!=len){
                dest.setstate(std::ios_base::badbit);
            }
        }
        return dest;
    }
    int main(){
    	#ifndef ONLINE_JUDGE
    	freopen("input.txt","r",stdin);
    	freopen("output.txt","w",stdout);
    	#endif
    	//driver code here
    	ll i , n, k, a, b, j;
    	unordered_map<ll,ll>mp;
    	cin>>n>>k>>a>>b;
    	mp[1]=k;
    	for(i=2; i<=n; i++){
    	    ll sum=0;
    	    for(j=1; j<=i-1; j++){
    	        sum=sum+(mp[j]*mp[i-j])%mod;
    	        sum%=mod;
    	    }
    	    sum=(sum*b)%mod;
    	    mp[i]=((a*mp[i-1])%mod+sum)%mod;
    	}
    	cout<<mp[n];
        return 0;
    } 
