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

