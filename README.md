# Optimal-Array
Given a sorted array, return the minimum number of operations to convert the array so that elements are equal.

<span style="font-size:18px">You are given a <strong>sorted</strong> array <strong>a</strong> of length<strong> n</strong>. For each <strong>i</strong>(0&lt;=i&lt;=n-1), you have to make all the elements of the array from index 0 till i<strong> equal</strong>, using minimum number of operations. In one operation&nbsp;you either <strong>increase </strong>or <strong>decrease</strong> the array element by <strong>1</strong>.</span>
<span style="font-size:18px">You have to return a <strong>list</strong> which contains the <strong>minimum</strong> number of operations for each i, to accomplish the above task.</span>

Here is my approach

In an array if we make all the elements equal to median then the number of operations will be minimised, so here we are going to use that idea only + there will be a prefix array.
For the odd elements the median is the mid element and for the even elements the median is the mean of mid elements. The array is already sorted, if not then do it

Sharing the coding approach:

``````
public long[] optimalArray(int n,int a[])
    {
        long[] pre = new long[n];
        pre[0]=a[0];
        
        for(int i=1;i<n;i++)
        pre[i]=pre[i-1]+a[i];
        
        long[] op = new long[n];
        op[0]=0;
        for(int i=1;i<n;i++){
            int sum =0;
            if(i%2==0){
                //list is odd length
                int mid = i/2;
                long mid_val = a[mid];
                
                sum+=(mid_val*(mid)-(pre[mid-1]));
                sum+=(pre[i]-pre[mid]-(mid_val*(mid)));
                
            }
            else{
                
               int mid = i/2;
               long mid_val = (a[mid]+a[mid+1])/2;
               
               sum+=(mid_val*(mid+1)-pre[mid]);
               sum+=(pre[i]-pre[mid]-(mid_val*(mid+1)));
                
            }
            op[i]=sum;
        }
        return op;
        
        
    }

`````

Time Complexity: 0(n)
Space Complecity: 0(n)

GFG Practise Link: https://practice.geeksforgeeks.org/contest/interview-series-69/problems/


