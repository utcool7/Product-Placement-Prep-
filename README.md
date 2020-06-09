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
