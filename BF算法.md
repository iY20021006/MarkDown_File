# BF算法

&emsp;BF算法，即暴力(Brute Force)算法，是普通的字符串[模式匹配](https://baike.baidu.com/item/模式匹配/1258334?fromModule=lemma_inlink)算法，BF算法的思想就是将目标串S的第一个字符与模式串T的第一个[字符](https://baike.baidu.com/item/字符/4768913?fromModule=lemma_inlink)进行匹配，若相等，则继续比较S的第二个字符和 T的第二个字符；若不相等，则比较S的第二个字符和T的第一个字符，依次比较下去，直到得出最后的匹配结果。BF算法是一种[蛮力算法](https://baike.baidu.com/item/蛮力算法/20831322?fromModule=lemma_inlink)。



```cpp
class Solution 
{
public:
    int strStr(string haystack, string needle)
     {
        int i=0;int j=0;
        while(i<str.size()&&j<sub.size())
        {
            if(str[i]==sub[j])
            {
                //字符相等
                i++;j++;
            }
            else
            {
                //字符不相等初始下标
                i=i-j+1;
                j=0;
            }
        }
        if(j==sub.size())
        {
            return i-j;
        }
    return -1;
    }
};
```

