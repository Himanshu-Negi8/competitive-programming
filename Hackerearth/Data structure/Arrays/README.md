


1.  


1 X 

Flip A[X] 
if(0) set to 1 else set to 0

Now 0 L R
consider the array from L to R
check if this last digit 1 or not , if it's a yes. print odd


```c  

#include <bits/stdc++.h>
using namespace std;

int main(){

    int flip,zero;
    int one,left,right;
    int N,Q;

    cin>>N>>Q;

    int A[N];


    for(int i=1;i<=N;i++){
        cin>>A[i];
    }


    cin>>zero>>flip;

    cin>>one>>left>>right;



    if(A[flip]==0){
        A[flip]=1;
    }
    else{
        A[flip]=0;
    }

    if(A[right]==1){
        cout<<"ODD";
    }
    else{
        cout<<"EVEN";
    }
    return 0;


}

```



2. Monk and welcome problem

```c  

#include <bits/stdc++.h>
using namespace std;

int main(){


    int n;
    cin>>n;

    int *A=(int*)malloc(n*sizeof(int));
    int *B=(int*)malloc(n*sizeof(int));
    int *C=(int*)malloc(n*sizeof(int));


    for(int i=0;i<n;i++){
        cin>>A[i];
    }
    for(int i=0;i<n;i++){
        cin>>B[i];
    }

    for(int i=0;i<n;i++){
        C[i]=A[i]+B[i];
    }


    for(int k=0;k<n;k++){
        cout<<C[k]<<" ";
    }

    return 0;


}

```




3. Micro and Array Update


```c++

#include <bits/stdc++.h>
using namespace std;

int main() {

    int n, t, k,small;
    cin >> t;
//    cin >> n >> k;
    vector<int> v;




    for (int i = 0; i < t; i++) {

        cin >> n >> k;
        int A[n];


        for (int p = 0; p < n; p++) {
            cin >> A[p];
        }




        small=*min_element(A,A+n);



        v.push_back(k-small);
    }


    for(auto x:v){
        if(x<0)
        {
            x=0;
            cout<<x<<" "<<endl;
        }
        else{
            cout<<x<<" "<<endl;
        }

    }


    return 0;


}

```


### Pairs having similar elements

1. 

```c++  
#include<bits/stdc++.h>
using namespace std;

long long SimilarElementsPairs (vector<int> A,int N) {
    // Write your code here
    vector< pair<int,int> > points;
    int count=0;

    for(int i=0;i<N;i++){
        for(int j=i+1;j<=N;j++){
            if((A[i]==A[j]+1 || A[j]==A[i]+1))
            {

                points.emplace_back(i+1,j+1);
                count+=1;
            }
        }
    }


    cout<<"*********"<<endl;
    int flag=0;

    for(int k=0;k<count;k++){
        cout<<points[k].first<<"   "<<points[k].second<<endl;
        for(int m=k+1;m<count;m++){
                if(points[k].second==points[m].second || points[k].second==points[m].first){
                   flag+=1;
                }
        }
    }
    return flag;

}

int main() {

    ios::sync_with_stdio(0);
    cin.tie(0);
    int N;
    cin >> N;
    vector<int> A(N);
    for(int i_A=0; i_A<N; i_A++)
    {
        cin >> A[i_A];
    }

    long long out_;
    out_ = SimilarElementsPairs(A,N);
    cout << out_;
}

```



2. The function ain't returning proper value

```c++

#include<bits/stdc++.h>
using namespace std;

long long SimilarElementsPairs (vector<int> A,int N) {
    // Write your code here
    vector< pair<long long,long long> > points;
    long long count=0;

    for(int i=0;i<N;i++){
        for(int j=i+1;j<=N;j++){
            if((A[i]==A[j]+1 || A[j]==A[i]+1))
            {
                points.emplace_back(i+1,j+1);
                count+=1;
            }
        }
    }


    int flag=0;
    for(int k=0;k<count;k++){
        for(int m=k+1;m<count;m++){
                if(points[k].second==points[m].second ) {
//                   cout<<points[k].second<<"  "<<points[m].second<<endl;
flag+=1;
                }
                 if( points[k].second==points[m].first)
            {
//                cout<<points[k].second<<"  "<<points[m].first<<endl;
flag+=1;
            }
             if(points[k].first==points[m].first){
//                cout<<points[k].first<<"  "<<points[m].first<<endl;
flag+=1;
            }
            else{

            }

        }
    }
    return flag+count;

}

int main() {

    ios::sync_with_stdio(0);
    cin.tie(0);
    int N;
    cin >> N;
    vector<int> A(N);
    for(int i_A=0; i_A<N; i_A++)
    {
        cin >> A[i_A];
    }

    long long out_;
    out_ = SimilarElementsPairs(A,N);
    cout << out_;
}

```




### Hamilton and lagrangian



1. **Try to improve time complexity**

```c++ 

#include <bits/stdc++.h>
using namespace std;


int main(){
    vector<int> v;
    int N,flag=0,element;
    int* A=(int *)malloc(sizeof(int)*N);
    cin>>N;
    for(int i=0;i<N;i++){
        cin>>A[i];
    }

//    iterate over array  add it in vector if it is smaller than rest of elements   in its right
//  i

    for(int i=0;i<N;i++){
        element=A[i];
        // for each A[i]  check whether all a[j] are smaller
        //  j=i+1
        for(int k=i+1;k<N;k++){
            if(A[k]>element){
                flag=1;
                break;
            }
        }
        if(flag==0){
            v.push_back(element);
        }
        flag=0;
    }


    for(auto x:v){
        cout<<x<<" ";
    }

}

```




### Charged Up Array


1. We need to generate subsets


```c++ 

#include <bits/stdc++.h>
using namespace std;



void printPowerSet(char *set,int set_size){
    unsigned int pow_set_size=pow(2,set_size);
    int counter,j;

    for(counter=0;counter<pow_set_size;counter++){
        for(j=0;j<set_size;j++){
            if(counter&(1<<j)){
                cout<<set[j];
            }
        }
        cout<<endl;
    }

}

int main(){
    char set[]={'a','b','c'};
    printPowerSet(set,3);

}



```



### Pending solution


1. Need to store one D vector in 2 D vector.

```c++
#include <bits/stdc++.h>
using namespace std;



void printPowerSet(int *set,int set_size){
    unsigned int pow_set_size=pow(2,set_size);
    vector <int> v;
    vector<vector<int>> wow;
    int counter,j;

    for(counter=0;counter<pow_set_size;counter++){
        for(j=0;j<set_size;j++){
            if(counter&(1<<j)){
                cout<<set[j];
                v.push_back(set[j]);
            }
        }
        wow.push_back(v);

        cout<<endl;
    }

    for(auto x:wow){
        for(auto y:x){
            cout<<y;
        }
        cout<<endl;
    }
}

int main(){
    int set[]={1,2,3};
    printPowerSet(set,3);

}


```









4. Polygon possibility

:heart:


**Property of a polygon is that sum of largest side is always smaller than sum of the
rest of the sides**


```c++


#include<bits/stdc++.h>
using namespace std;


int main() {

    int T, N;
    vector<int> values;
    vector<string> answers;
    int sum = 0, rest = 0;
    int element;
    int maximum;

    cin >> T;


    for (int i = 0; i < T; i++) {
        cin >> N;

        for (int j = 0; j < N; j++) {
            cin >> element;
            values.push_back(element);
        }
        sum = accumulate(values.begin(), values.end(), 0);
        maximum = *max_element(values.begin(), values.end());
        rest = sum - maximum;

        if (maximum < rest) {
            answers.emplace_back("Yes");
        } else {
            answers.emplace_back("No");
        }

        rest=0;
        sum=0;
        maximum=0;
        values.clear();
        N=0;
    }

    for(auto x:answers){
        cout<<x<<endl;
    }


//   find max(elements)
//   check if max<sum of all elements other than max
//   sum of rest elements  sum(elements)-max;
//   if   yes,  print Yes else No


}



"A:\Competitive programming\Cplusplusworkbench\cmake-build-debug\Cplusplusworkbench.exe"
2
3
4 3 2
4
1 2 1 42
3
4 3 2
4
1 2 1 4

Yes
        No



Process finished with exit code 0



```



### Pending 


#### Neutralisation of charges



```c++







// iterate over the strings

// the each character you get check whether its
//neighbour is same , if same then remove both
// now aaacccbbcccd   i=0
//     aa   acccbbcccd i=1
//      cc  acbbcccd  i=2

#include <bits/stdc++.h>
using namespace std;
int main(){
    string value;
    getline(cin,value);




    for(int i=0;i<value.size();i++){
        for(int j=0;j<i+1;j++) {
            if (value[i] == value[j]) {
                value.erase(value.begin() + i, value.begin() + i + 2);
            }
            else{
                break;
            }
        }
    }

    for(auto x:value){
        cout<<x;
    }



    return 0;
}


```





# Takeoff



**debugged code**

```c++  
#include <bits/stdc++.h>

using namespace std;
int main(){
    int T;
    int N,p,q,r;
    vector<int> answer;
    int *A,*B,*C;
    int fly=0;
    int flag=0;
    int another,element;

    cin>>T;

    for(int i=0;i<T;i++){

        cin>>N>>p>>q>>r;
        A=(int *)malloc(sizeof(int)*N);
        B=(int *)malloc(sizeof(int)*N);
        C=(int *)malloc(sizeof(int)*N);

        for(int j=0;j<N;j++){
            A[j]=(p*(j+1));
            B[j]=(q*(j+1));
            C[j]=(r*(j+1));
        }



        for(int m=0;m<N;m++){
            flag=0;
            element=A[m];

            if(element<=N ) {
                for (int k = 0; k < N; k++) {
                    if (element == B[k] || element==C[k]) {
                        flag = 1;
                        break;
                    }
                }
            }
            if (flag == 0&&element<=N) {
                fly += 1;
                cout<<"****"<<endl;
                cout<<element<<"   "<<endl;
                cout<<"****"<<endl;
            }
        }




        for(int m=0;m<N;m++){
            flag=0;
            another=B[m];

            if(another<=N ) {
                for (int k = 0; k < N; k++) {
                    if (another == C[k]||another==A[k]) {
                        flag = 1;
                        break;
                    }
                }
            }
            if (flag == 0&&another<=N) {
                fly += 1;
                cout<<"****"<<endl;
                cout<<another<<"   "<<endl;
                cout<<"****"<<endl;

            }
        }














        answer.push_back(fly);
        fly=0;
        free(A);
        free(B);
        free(C);



    }


    for(auto x:answer){
        cout<<x<<" ";
    }


}

```




**FInal one** :heart:  :smile:





**Fix this**

```c++

#include <bits/stdc++.h>

using namespace std;

int min(int a,int b,int c){
    if(a<b && a<c){
        return a;
    }
    else if(b<c&&b<a){
        return b;
    }
    else{
        return c;
    }
}
int main() {
    int T;
    int N, p, q, r;
    vector<int> answer;
    int *A, *B, *C;
    int fly = 0;
    int flag = 0;
    int another, element;
    int one=0,two=0,three=0;
    int minimum;

    cin >> T;

    for (int i = 0; i < T; i++) {

        cin >> N >> p >> q >> r;
        minimum=min(p,q,r);

        A = (int *) malloc(sizeof(int) * N);
        B = (int *) malloc(sizeof(int) * N);
        C = (int *) malloc(sizeof(int) * N);

        for (int j = 0; j < N; j++) {

            if (minimum * (j + 1) <= N) {
                minimum = (j + 1) * minimum;


            if (p * (j + 1) <= N) {
                A[j] = (p * (j + 1));
                one += 1;

            }

            if (p * (j + 1) <= N) {
                B[j] = (q * (j + 1));
                two += 1;
            }

            if (p * (j + 1) <= N) {
                C[j] = (r * (j + 1));
                three += 1;
            }
        }
            else{
                break;
            }

        }

        for(int u=0;u<one;u++){
            cout<<A[u];
        }
        cout<<endl;
        for(int u=0;u<two;u++){
            cout<<B[u];
        }
        cout<<endl;
        for(int u=0;u<three;u++){
            cout<<C[u];
        }

    }
}



```




## Long atm queue


```c++

#include <bits/stdc++.h>
using namespace std;

int main(){
    int N,element,count=0;
    cin>>N;
    int *height=(int *)malloc(sizeof(int)*N);

    for (int i = 0; i < N; ++i) {
        cin>>element;
        height[i]=element;
    }

    for (int j = 0; j < N; ++j) {
        if(height[j]>height[j+1]){
            count+=1;
        }
    }
    
    cout<<count;
    return 0;
}

```



### Best submission


1. We don't even need to store the elements in the array. Just take the input save it  then compare with next input.

```c++  
    #include <bits/stdc++.h>
     
    using namespace std;
     
    typedef signed long long ll;
    typedef pair<int, int> pii;
    const int MX = 1e6 + 5;
    int A[MX], B[MX];
     
    int main(){
    	int n, num, prev = -1, cnt = 0;
    	scanf("%d", &n);
     
    	for(int i = 0; i < n; i++){
    		scanf("%d", &num);
    		if(i == 0){
    			cnt++;
    			prev = num;
    		}else{
    			if(prev > num){
    				cnt++;
    			}
    			prev = num;
    		}
    	}
    	printf("%d\n", cnt);
     
    	return 0;
    }

```


### Optimizations



:fire:  :fire:  :fire:



```c++  


#include <bits/stdc++.h>
using namespace std;

int main(){
    int N,element,count=0,prev=-1;
    cin>>N;


    for (int i = 0; i < N; ++i) {
        cin>>element;
        if(i==0){
            count=1;
            prev=element;
        }

        if(prev>element){
            count+=1;
        }

        prev=element;

    }


    cout<<count;
    return 0;
}

```




:clap:



```c++ 
if(i == 0){
   count++;
   	prev = num;
   		}
   	     else{
    		if(prev > num){
    				count++;
    			}
    			prev = num;
    		}
    		
 ```




---





### Maximize the earning


```c++


#include <bits/stdc++.h>
using namespace std;

int main(){
    int max=-1;
    int S,N,R;

    int element;
    int count=0;
    int *height;

    cin>>S;
    vector<int> answer;

    for(int i=0;i<S;i++){
        cin>>N>>R;
        height=(int *)malloc(sizeof(int)*N);
        for (int j = 0; j < N; ++j) {
            cin>>element;
            height[j]=element;

        }

        for(int k=0;k<N;++k){
            element=height[k];
            if(max<element){
                max=element;
                count+=1;
            }
        }
        answer.push_back(count*R);
        max=-1;
        count=0;
        free(height);


    }

    for(auto x:answer){
        cout<<x<<endl;
    }

}

```




**I did this right** 

*We don't really have to save the height in an array*

---

**But this isn't making any difference**

---


```c++


#include <bits/stdc++.h>
using namespace std;

int main(){
    int max=-1;
    int S,N,R;

    int element;
    int count=0;

    cin>>S;

    for(int i=0;i<S;i++){
        cin>>N>>R;
        for (int j = 0; j < N; ++j) {
            cin>>element;
            if(element>max){
                max=element;
                count+=1;
            }
        }
        cout<<count*R<<endl;
        count=0;
        max=-1;
    }

}

```


#### Best submission ??? 

:wink:


```c++


    #include <bits/stdc++.h>
    #define endl "\n"
    #define ll long long
    #define fast ios_base::sync_with_stdio(0),cin.tie(NULL),cout.tie(NULL)
    using namespace std;
    ll scan() 
    {
        register int c; 
        ll number = 0;
        c = getchar_unlocked(); 
        for (; (c>47 && c<58); c=getchar_unlocked()) 
            number = number *10 + c - 48; 
        return number;
    } 
    int main()
    {
        int t;      t=scan();
        while(t--)
        {
            int n, r;    ll arr[100001], m = 0, max = 0;
            n=scan();    r=scan();
            for(int i=0; i<n; i++)
            {
                arr[i] = scan();
                if(arr[i] > max)
                {
                    max = arr[i];
                    m++;
                }
            }
            cout<<m*r<<endl;
        }
    }


```


---








---



**Zarvis**

```c++


#include <bits/stdc++.h>
using namespace std;

int main(){
    int remainder;
    int element=1324,t;
    vector<int> value;
    for(int k=0;k<t;k++) {

        cin>>element;
        value.push_back(element);

        while (element != 0) {
            remainder = element % 10;
            value.push_back(remainder);
            element /= 10;
        }

        sort(value.begin(), value.end());


        for (auto x:value) {
            cout << x;
        }
        int flag = 0;

        for (int i = 1; i < value.size(); i++) {
            if (value[i] - value[i - 1] != 1) {
                cout << "No";
                flag = 1;
                break;
            }
        }
        if (flag == 0) {
            cout << "Yes";
        }
    }

}  

```




### Snackdown contest

:-1:

```c++
#include <bits/stdc++.h>
using namespace std;

int main(){


        int T,N,P,Q;
        int *solved,*another,*empty;
        int flag=0;
        int count=0,within=0;
        cin>>T;
        for(int i=0;i<T;i++){

            cin>>N;
            cin>>P;
            solved=(int *)malloc(sizeof(int)*P);
            for(int j=0;j<P;j++){
                cin>>solved[j];
            }
            cin>>Q;
            another=(int *)malloc(sizeof(int)*Q);
            for (int k = 0; k < Q; ++k) {
                cin>>another[k];
            }


            empty=(int *)malloc(sizeof(int)*N);

            int l;
            for (l = 0; l < P; ++l) {
                empty[l]=solved[l];
            }

            for (int n = 0; n < Q; ++n) {
                empty[l+n]=another[n];
            }

            sort(empty,empty+(P+Q));
//            cout<<"***";
//            for(int pp=0;pp<P+Q;pp++){
//                cout<<empty[pp]<<"  ";
//            }
//            cout<<"***";
            for (int i1 = 1; i1 < P+Q; ++i1) {
                if(empty[i1]==empty[i1-1]){
                    within+=1;
                    continue;
                }
                else{
                    if(empty[i1]-empty[i1-1]!=1){
                        flag=1;
                        break;
                    }
                    count+=1;
                }
            }
//            cout<<"Within"<<within<<"count"<<count<<"count+within/2  ="<<(count+(within)/2);
            if(flag==0 && (count+within)==N){
                cout<<"Yes"<<endl;
            }
            else{
                cout<<"No"<<endl;
            }
            within=0;
            count=0;
            flag=0;
            P=0;
            Q=0;
            free(another);
            free(empty);
            free(solved);

        }


        return 0;


}

```




```c++

#include <bits/stdc++.h>
using namespace std;

int main(){


        int T,N,P,Q;
        int *solved,*another;
        set<int> empty;

        vector<int> emp;
        cin>>T;
        for(int i=0;i<T;i++){

            cin>>N;
            cin>>P;
            solved=(int *)malloc(sizeof(int)*P);
            for(int j=0;j<P;j++){
                cin>>solved[j];
            }
            cin>>Q;
            another=(int *)malloc(sizeof(int)*Q);
            for (int k = 0; k < Q; ++k) {
                cin>>another[k];
            }

            for(int p=0;p<P;p++){
                empty.emplace(solved[p]);
            }
            for(int l1=0;l1<Q;l1++){
                empty.emplace(another[l1]);
            }


            if(empty.size()==N){
                cout<<"YES";
            }
            else{
                cout<<"NO";
            }
            cout<<endl;



            P=0;
            Q=0;
            free(another);
            free(solved);
            empty.erase(empty.begin(),empty.end());
        }


        return 0;


}
```



### Best submission


**Initialize an empty array of size N,Set the question to 1 if solved**

```c++
#include<bits/stdc++.h>
using namespace std;
int main()
{
    int t;
    cin>>t;
    while(t--)
    {
        bool f = false;
        long long int n,a,b;
        cin>>n;
        int arr[n+1]={0};
        cin>>a;
        for(int i=0;i<a;i++)
        {
            long long int num;
            cin>>num;
            arr[num]=1;
        }
        cin>>b;
        for(int i=0;i<b;i++)
        {
            long long int num;
            cin>>num;
            arr[num] = 1;
        }
        for(int i=1;i<=n;i++)
        {
            if(arr[i]==0)
            {
                cout<<"NO"<<"\n";
                f=true;
                break;
            }
        }
        if(f==false)
            cout<<"YES"<<"\n";
    }
}
```



# Final submission 

**The values are large enough use long , lld**

```c++
#include <bits/stdc++.h>

typedef long long int lld;
using namespace std;

int main(){

    int T,N,K;
    int *Alice;
    int *Bob;
    lld maximum=-1;
    lld answer=0;
    cin>>T;

    while (T>0){

        cin>>N>>K;
        Alice=(int *)malloc(sizeof(int)*N);
        Bob=(int *)malloc(sizeof(int)*N);

        for(long i=0;i<N;i++){
            cin>>Alice[i];
        }


        for(long i=0;i<N;i++){
            cin>>Bob[i];
        }


        maximum=*max_element(Bob,Bob+N)+1;
        for(long k=0;k<N;k++){
            if(Alice[k]<maximum)
            {
                answer+=((maximum-Alice[k])*K);
            }
        }
        cout<<answer<<endl;
        answer=0;
        maximum=-1;
        free(Alice);
        free(Bob);
        T--;
    }

}


```



### Misc

**size_t and npos**


```c++

// CPP program to demonstrate working of string
// find to search a string
#include <iostream>
#include <string>

using namespace std;

int main()
{

    string first="hello  how are you  , hello ";
    string second="hello";

    int found=first.find(second);
    if(found != string::npos){
        cout<<"found at "<<found; 
    }
    return 0;
}


```


### Medium


1. Can you solve it

```c++

#include <bits/stdc++.h>

using namespace std;

int main()
{
    int T;
    cin>>T;

    int N;
    int max=-1;

    while(T>0){

        cin>>N;
        int *values=(int *)malloc(sizeof(int)*N);
        for (int i = 0; i < N; ++i) {
            cin>>values[i];
        }

        for(int i=0;i<N-1;i++){
            for (int j = i+1; j < N; ++j) {
                if(abs(i-j)+abs(values[i]-values[j])>max){
                    max=abs(i-j)+abs(values[i]-values[j])>max;
                }
            }

        }
        cout<<max<<endl;

        free(values);
        max=-1;



        T--;
    }

    return 0;
}


```



### Jarvis 


1. Partial submission

```c++

#include <bits/stdc++.h>

using namespace std;

int main() {

    int T;
    vector<int> coaches;
    int remainder=0;
    int element,count=0,flag=0;
    cin>>T;

    while(T>0){
        cin >> element;
        while (element != 0) {
            remainder = element % 10;
            coaches.push_back(remainder);
            element /= 10;
            count += 1;
        }
        sort(coaches.begin(), coaches.end());
        for (int m = 0; m < count; m++) {
            if (abs(coaches[m] - coaches[m - 1]) != 1) {
                flag = 1;
                cout << "NO" << endl;
                break;
            }
        }
        if(flag==0) {
            cout << "YES" << endl;
        }
        coaches.erase(coaches.begin(), coaches.end());
        flag = 0;
        count = 0;
        element = 0;
        T--;
    }



}

//    while taking input check
//    u don't really have to store the elements
//    take  in put for  just push_back the individual elements right away.
//    sort this  now if the difference between the elements!=1 break .


```


:+1:







---


:heart:


:yellow_heart:

**I did it**


```c++

#include <bits/stdc++.h>
using namespace std;

int main(){
    int t;
    cin>>t;
    int flag=0;
    string s;
    for(int i=0;i<t;i++){
        cin>>s;
        sort(s.begin(),s.end());

        for(int i=0;i<s.size()-1;i++){
            if(((s[i+1]-'1'+1)-(s[i]-'1'+1))!=1){
//                cout<<(s[i+1]-'1'+1)<<"  "<<(s[i]-'1'+1)<<"   "<<endl;
//                cout<<"NO  "<<(s[i+1]-'1'+1)-(s[i]-'1'+1)<<endl;
                cout<<"NO"<<endl;
                flag=1;
                break;
            }
        }

//        cout<<"WTF"<<flag<<endl<<s;

        if(flag==0){cout<<"YES"<<endl;}
        flag=0;
        s.erase(s.begin(),s.end());
    }
    return 0;
}


```


---

### More intuitive way is to use somewhat like hash

```c++
    #include<bits/stdc++.h>
    using namespace std;
    int main(){
        int t;
        cin>>t;
        while(t--){
            int n,a[10]={0},mi=INT_MAX,ma=INT_MIN,i=0;
            string s;
            cin>>s;
            while(i<s.length()){
                mi=min(mi,s[i]-'1'+1);
                ma=max(ma,s[i]-'1'+1);
                a[s[i]-'1'+1]+=1;
                i++;
            }
            for(i=mi;i<=ma;i++){
                if(a[i]!=1){
                    cout<<"NO\n";
                    break;
                }
            }
            if(i==ma+1)
            cout<<"YES\n";
        }
    }


```

---



# This approach gives you the occurence of each character in string,number

---

```c++

#include <bits/stdc++.h>
typedef long long int lld;
using namespace std;


int main() {
     int i=0;
     int minimum=INT_MAX;
     int maximum=INT_MIN;
     string s;
     int a[10]={0};
     cin>>s;


     while (i<s.length()){
         minimum=min(minimum,s[i]-'1'+1);
         maximum=max(maximum,s[i]-'1'+1);
         a[(s[i]-'1'+1)]+=1;
         i++;
     }

     for(int i=minimum;i<=maximum;i++){
         cout<< a[i]<<"  ";
     }


}

//    while taking input check
//    u don't really have to store the elements
//    take  in put for  just push_back the individual elements right away.
//    sort this  now if the difference between the elements!=1 break .



```


---





## Monk and power of time . I did bad.           :(

```c++
#include<iostream>
#include<queue>
using namespace std;
 
int main()
{
    int n,m;
    cin >> n;
    
    queue<int> calling,ideal;
    
    for(int i=0;i<n;i++)
    {
        cin >> m;
        calling.push(m);
    }
    
    for(int i=0;i<n;i++)
    {
        cin >> m;
        ideal.push(m);
    }
    long long int count=0;
    
    while(!calling.empty())
    {
        if(calling.front() == ideal.front())
        {
            count++;
            calling.pop();
            ideal.pop();
        }
        else
        {
            int val = calling.front();
            calling.pop();
            calling.push(val);
            count++;
        }
    }
    
    cout << count << endl;
    
    
    return 0;
}

```




### Fix

```c++

#include <bits/stdc++.h>
using namespace std;

int main() {

    queue<int> calling;
    queue<int> ideal;
    int data;
    int count=0;

    int N;
    cin>>N;

    for(int i=0;i<N;i++){
        cin>>data;
        calling.push(data);
    }


    for(int m=0;m<N;m++){
        cin>>data;
        ideal.push(data);

    }

    while (!ideal.empty()){

        if(ideal.front()==calling.front()){
            count+=1;
            ideal.pop();
            calling.pop();
        }
        else{
             int callingFront=calling.front();
             calling.pop();
             calling.push(callingFront);
             count+=1;
        }

    }

    cout<<count;




}
//
//int i=0;
//int minimum=INT_MAX;
//int maximum=INT_MIN;
//string s;
//int a[10]={0};
//cin>>s;
//
//
//while (i<s.length()){
//minimum=min(minimum,s[i]-'1'+1);
//maximum=max(maximum,s[i]-'1'+1);
//a[(s[i]-'1'+1)]+=1;
//i++;
//}
//
//for(int i=minimum;i<=maximum;i++){
//cout<< a[i]<<"  ";
//}


```




### Misc

**Rotate a string**

```c++

// C++ program to demonstrate working of rotate
#include <bits/stdc++.h>
using namespace std;

int main()
{
    string str = "ABCD";

    // Rotating arround second element
    // string becomes "BCDA"
    rotate(str.begin(), str.begin()+1, str.end());
    cout << str << endl;

    // Again rotating around second element
    // string becomes "CDAB"
    rotate(str.begin(), str.begin()+1, str.end());
    cout << str<<endl;

//    rotate around second again

    rotate(str.begin(),str.begin()+1,str.end());
    cout<<str;

    return 0;
}


```


---

:mountain:

1. This is to print power set.


```c  
#include <bits/stdc++.h>
using namespace std;


void checksubstring(int *string,int n){

    unsigned  int power=pow(2,n);
    for(int i=0;i<power;i++){
        for(int j=0;j<n;j++){
            if(i&(1<<j)){
                cout<<string[j];
            }
        }
        cout<<endl;
    }
}

int main(){

    int string[]={1,2,3};
    checksubstring(string,3);

    return 0;
}

```



---



---

### Charged Up array

**first**

```c  
#include <bits/stdc++.h>
using namespace std;


int checksubstring(int *values,int n){
    unordered_map<int,int> H;
    int total=0;


    unsigned  int power=pow(2,n);
    for(int i=0;i<power;i++){
        for(int j=0;j<n;j++){
            if(i&(1<<j)){
//                cout<<values[j];
                H[values[j]]++;

            }
        }
//        cout<<endl;
    }


//    cout<<"commonmmmmmmmmmmmmmmmmmmmmmmmmmmmmmn"<<endl;
    for(auto x:H){
//        cout<<x.first<<" appears "<<x.second<<" times  "<<endl;
        if(x.first>=x.second)
            total+=x.first;
    }
    return total;
}



int main(){
    int t,n;
    int *values;
    cin>>t;

    while (t!=0){

        cin>>n;
        values=(int *)malloc(sizeof(int)*n);
        for(int i=0;i<n;i++){
            cin>>values[i];
        }
        cout<<checksubstring(values,n);

        free(values);

        --t;
    }
    return 0;
}


//unordered_map<char,int> H;
//for (int i = 0; i < s.length(); ++i) {
//H[s[i]]++;
//}


```

---



### Charged up array

```c++
#include<bits/stdc++.h>
using namespace std;
#define M 1000000007

int solve (vector<long long> values) {
    // Write your code here
    long long n=values.size();
    unordered_map<long long ,long long > H;
    long long int total=0;

    long long  power=pow(2,n);
    for(long long i=0;i<power;i++){
        for(long long j=0;j<n;j++){
            if(i&(1<<j)){
                H[values[j]]++;
            }
        }

    }

//    (a+b) mod m = (a mod m+b mod m) mod m

    for(auto x:H){

        if(x.first>=x.second)
            total=(total%M + x.first%M)%M;
    }
    return total;

}

int main() {

    ios::sync_with_stdio(0);
    cin.tie(0);
    int T;
    cin >> T;
    for(int t_i=0; t_i<T; t_i++)
    {
        int N;
        cin >> N;
        vector<long long> A(N);
        for(int i_A=0; i_A<N; i_A++)
        {
            cin >> A[i_A];
        }

        int out_;
        out_ = solve(A);
        cout << out_;
        cout << "\n";
    }
}
```