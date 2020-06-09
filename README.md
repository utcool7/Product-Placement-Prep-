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

**2) 75. Sort Colors ( leetcode ) **

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
