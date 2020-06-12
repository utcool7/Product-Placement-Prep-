# DAY 1( 9 June 2020 )   

**1) 442. Find All Duplicates in an Array (leetcode)**


    class Solution {
    public:
    vector<int> findDuplicates(vector<int>& nums) {
        
        vector <int> res;
        
        for( int i = 0 ; i < nums.size() ; i++ )
        {
            int index = abs(nums[i]) - 1;
            if( nums[index] < 0 )
                res.push_back( index + 1 );
            
            nums[index] = -nums[index];
            
        }  
        
        return res;
    }
   };

**2) 75. Sort Colors ( leetcode )**

    class Solution {
    public:
     void sortColors(vector<int>& nums) {
        int low = 0 , mid = 0;
        int high = nums.size() - 1 ;
        
        while( mid  <= high )
        {
            if( nums[mid] == 0 )
            {
                swap(nums[mid] , nums[low]);
                low++;
                mid++;
            }  
            
            else if( nums[mid] == 1)
                mid++;
            
            else if( nums[mid] == 2 )
            {
                swap(nums[mid] , nums[high]);
                high--;
            }
          
            
        }
        
    }
    };

**3) 268. Missing Number(leetcode)**

     class Solution {
     public:
      int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int act = n*(n+1)/2;
        int sum = 0 ;
        for(int i= 0; i<n;i++)
            sum+=nums[i];
        return act-sum;
        
    }
    };
    
**4) Kadanes Algo( largest sum contiguous subarray )**


     int kadane(int arr[], int n)
     {
      
       int max_so_far = INT_MIN ;
       int max_end_here = 0;
       for(int i = 0 ;i < n; i++)
       {
          max_end_here+=arr[i];
        
        if(max_end_here < arr[i])
        {
            max_end_here = arr[i];
            
        }
        if(max_so_far < max_end_here)
        {
            max_so_far = max_end_here ;
        }
        
      }
    
      return max_so_far;
    } 

**5) 88. Merge Sorted Array(leetcode)**

     class Solution {
     public:
      void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        
        int count = m + n - 1 ;
        m = m - 1;
        n = n - 1 ;
        
        while(m >= 0 && n >= 0)
        {
            if( nums1[m] > nums2[n] )
                nums1[count--] = nums1[m--];
            else
                nums1[count--] = nums2[n--];
        }
        while( n >= 0 )
            nums1[count--] = nums2[n--];
        
    }
    };


# DAY 2( 10 June 2020 )  

**1) 118. Pascal's Triangle(leetcode)**


    class Solution {
    public:
     vector<vector<int>> generate(int numRows) {
        vector<vector<int>> res;
        if(numRows == 0)
            return res ;
        if( numRows == 1 ){
            res.push_back({1});
            return res;
        }
        
        res.push_back({1});
        res.push_back({1,1});
        
        if( numRows == 2 ){
            return res;   
        }
        for( int i = 2 ; i < numRows ; i++)
        {
            vector <int> temp(i+1,1);
            for( int j = 1 ; j < i ; j++)
            {
                    temp[j] = (res[i-1][j] + res[i-1][j-1]);   
            }
            res.push_back(temp);
        }
        return res;
    }
    };

**2) 31. Next Permutation(leetcode)**

1. Find the largest index k such that nums[k] < nums[k + 1]. If no such index exists, just reverse nums and done.
2. Find the largest index l > k such that nums[k] < nums[l].
3. Swap nums[k] and nums[l].
4. Reverse the sub-array nums[k + 1:].


       class Solution {
       public:
       void nextPermutation(vector<int>& nums) {
        int n = nums.size(), k, l;
    	for (k = n - 2; k >= 0; k--)
        {
            if (nums[k] < nums[k + 1]) 
            {
                break;
            }
        }
    	if (k < 0)
        {
    	    reverse(nums.begin(), nums.end());
    	}
        else
        {
    	    for (l = n - 1; l > k; l--) 
            {
                if (nums[l] > nums[k]) 
                {
                    break;
                }
            } 
    	    swap(nums[k], nums[l]);
    	    reverse(nums.begin() + k + 1, nums.end());
        }
       }
       };

**3) 48. Rotate Image( leetcode )**

    class Solution {
    public:
    void rotate(vector<vector<int>>& matrix) {
        int m = matrix.size(),n = matrix[0].size();
        for(int i=0;i<m;i++)
        {
            for(int j=i;j<n;j++)
            {
                if(i!=j)
                  swap(matrix[i][j],matrix[j][i]);
            }
        }
        for(int i=0;i<m;i++)
        {
            for(int j=0;j<n/2;j++)
                swap(matrix[i][j],matrix[i][n-j-1]);
        }
       
        
    }
    };
    
**4) 121. Best Time to Buy and Sell Stock(leetcode )**


    class Solution {
    public:
    int maxProfit(vector<int>& prices) {
        int minPrice = INT_MAX;
        int maxProfit = 0;
        for(int i = 0 ; i < prices.size() ; i++)
        {
            if(prices[i] < minPrice)
                minPrice = prices[i];
            else if(prices[i] - minPrice > maxProfit)
                maxProfit = prices[i] - minPrice;
        }
        return maxProfit;
    }
    };
    
**5) 73. Set Matrix Zeroes (leetcode)**

    class Solution {
    public:
    void setZeroes(vector<vector<int>>& matrix) {
        
        int m = matrix.size();
        int n = matrix[0].size();
        int firstRow = false ;
        int firstCol = false;
        
        for(int i = 0 ; i < m ; i++)
        {
            if( matrix[i][0] == 0 )
                firstCol = true ;
        }
        
        for(int i = 0 ; i < n ; i++)
        {
            if( matrix[0][i] == 0 )
                firstRow = true ;
        }
        
        for(int i = 0 ; i < m ; i++)
        {
            for(int j = 0 ; j < n; j++)
            {
                if(matrix[i][j] == 0)
                {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }
         for(int i = 1 ; i < m ; i++)
        {
            for(int j = 1 ; j < n; j++)
            {
                if(matrix[i][0] == 0 || matrix[0][j] == 0)
                {
                    matrix[i][j] = 0;
                }
            }
         }
        
        if(firstCol == true)
        {
            for(int i = 0 ; i < m ; i++)
                matrix[i][0] = 0 ;
        }
        
        if(firstRow == true)
        {
            for(int i = 0 ; i < n ; i++)
                matrix[0][i] = 0 ;
        }
        
    }
    };

# DAY 3( 11 June 2020 ) 

**1) 172. Factorial Trailing Zeroes ( leetcode )**

    class Solution {
    public:
    int trailingZeroes(int n) {
        int zeroes = 0;
        while( n )
        {
            zeroes += n/5;
            n = n/5;
        }
            
        return zeroes;
    }
    };
    
 **2) GCD of two numbers**
 
    //time :O(log(min(a,b)))
    int gcd(int a, int b) 
    { 
      if (b == 0) 
          return a; 
      return gcd(b, a % b);  
      
    } 
   
# DAY 4( 12 June 2020 ) 

**1) 50. Pow(x, n) ( leetcode )**

    class Solution {
    public:
    double myPow(double x, long long n) {
        
        if( n == 0 )
            return 1;
        
        if(n == 1)
            return x ;
        
        if( n < 0 )
           return  1 / myPow( x , -n );
        
        double temp = myPow( x, n/2 );
        
        if( n % 2 == 0 )
        {
            return temp * temp ;
        }
        else 
            return temp * temp * x;  
            
    }
    };
    
**2) 1. Two Sum ( leetcode )**

    class Solution {
    public:
    vector<int> twoSum(vector<int>& nums, int target) {
        
        vector <int> res(2);
        map <int , int > mp;
        for(int i = 0 ; i < nums.size() ; i++)
            mp[nums[i]] = i;
        
        for(int i = 0 ; i < nums.size() ; i++)
        {
            int numberToFind = target - nums[i] ;
            if(mp[numberToFind] && mp[numberToFind] != i)
            {
                res[0] = i;
                res[1] = mp[numberToFind];
            }
        }
        return res;
    }
    };
