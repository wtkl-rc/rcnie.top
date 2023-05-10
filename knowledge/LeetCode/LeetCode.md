#  27.移除元素

```c++
暴力破解法
程序不能运行
int removeElement(vector<int>& nums, int val) {
    int i;
    int k=sizeof(nums)-1;        //数组长度
    for(i=0;i<=k;i++){            //遍历数组
        if(nums[i]==val){
            for(int j=i;j<k;j++){            //移动数组
                    nums[j]=nums[j+1];
            }
            k--;
            i--;
        }
    }
    return k;
  }
```

```
双指针法
快慢指针法
用的就是两个指针，一个快指针和一个慢指针，开始时两个指针同时移动，移动到目标元素后，慢指针不动，快指针移动。慢指针的元素变为快指针的元素，实现元素替换。
int removeElement(vector<int>& nums, int val) {
	    int slowIndex = 0;
        for (int fastIndex = 0; fastIndex < nums.size(); fastIndex++) {
            if (val != nums[fastIndex]) {
                nums[slowIndex++] = nums[fastIndex];
            }
        }
        return slowIndex;
}
```

这段代码触及到了我的知识盲区，不知道如何去接受这样的新事物，我只能说，我尽力去了解它

# 977.有序数组的平方

第一个想法：直接先平方后排序

```
#include <vector>
#include <iostream>
using namespace std;

class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        int k;
        int i=0;
        int length =nums.size();
        for(i=0;i<length;i++){   //遍历数组
            nums[i]=nums[i]*nums[i];
        }

        for(k=length;k!=1;k--){
            for(i=0;i<k-1;i++){
                if(nums[i]>nums[i+1]){
                int j=nums[i];
                nums[i]=nums[i+1];
                nums[i+1]=j;
                }
            } 
        }

        return nums;
    }
};
```

这个算法理论上来说是可以的，但是算法时间复杂度太高，所以力扣不通过，后续优化一下。

问题：

1.排序不会，研究排序花了点时间

2.对于sizeof和.size的区别

总花费大约1小时

别人的代码优化：

```
class Solution {
public:
    vector<int> sortedSquares(vector<int>& nums) {
        int k;
        int i=0;
        int length =nums.size();
        for(i=0;i<length;i++){   //遍历数组
            nums[i]*=nums[i];
        }
     sort(nums.begin(), nums.end()); // 快速排序
        return nums;
    }
};
```

用sort函数

209.长度最小的子数组

在数组中找到  数组连续元素之和  为大于或等于target的最小子数组