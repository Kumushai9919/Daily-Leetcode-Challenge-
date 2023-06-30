# Day1  
## 49. Group Anagrams 
###### Medium  | <a href="https://leetcode.com/problems/group-anagrams/description/">leetcode link </a> | Array Hash Table String Sorting



#### 1. Introduction:
In the problem of grouping anagrams, we are given an array of strings - **strs**. Our task is to group the anagrams together and return the result. An **anagram** is a word or phrase formed by rearranging the letters of another word or phrase, using all the original letters exactly once. Here, we will discuss an efficient solution to this problem using a HashMap.
##### Example 1:
````
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
````

#### 2. Logic:
The logic behind our solution is to group words that are anagrams together in the strs array and return it. 
To identify anagrams, we have multiple ways to do, for instance the Sorting, we can sort each string in the array and check if sorting strings are anagrams, but it will take ```O(m * nlogn)``` time complexity where **n** is average length of each input strings and that's how much it takes to sort each strings, and we have to do that **m** times, it's basically the length of input strings in the array. So can we do better? 
Yes, we can also to compare the occurrence of characters in each word by counting the occurrences of each character in a word using an array. For efficient mapping of anagrams, we will use a HashMap.

#### 3. Explanation:
1. Crouping Anagrams:
We would group anagrams by counting the occurrences of each character in a word using **count[]** array. We know that we have at most 26 unique characters, and one of the condition also is that each character is gonna be from lowercase a to lowercase z **a-z**, so we can create array **count**, and let's take first string ```"eat"``` in the example:
```strs = ["eat","tea","tan","ate","nat","bat"]``` and count characters from a to z ```count[a-z] = 1e, 1a, 1t ```:

 ![IMG_FDDD62285DE5-1](https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/4c2f9669-6626-47f4-b805-d4cdc605fbdd)

Here, each index in the count array corresponds to a specific character, where index 0 represents 'a', index 1 represents 'b', and so on. And by iterating through the characters of ```"eat"```, we encounter 'e', 'a', and 't' and get the corresponding indices in the **count** array which we can use as a unique **key** to map anagrams in Hashmap, and our value is going to be the list of anagrams, in our case ```"eat", "tea", "ate"``` are going to be strings of values.

3. Mapping Anagrams:
We create a HashMap called ** "map"** to store the mapping  of **key** and **value** of anagrams, for each word in the **strs** array, we create the ```key``` by converting its ```count``` array to a string. If the key already exists in the **map**, we add the word to the corresponding group. Otherwise, we create a new ArrayList and add the word as the first element, mapping it to the key.

![IMG_F097D19E7060-1](https://github.com/Kumushai9919/Daily-Leetcode-Challenge-/assets/83897840/6efaf825-c745-4ed7-b799-2349470e5ffb)

Once we have grouped all the anagrams, we add the values (anagram groups) from the **map** to the **res** ArrayList which contains anagram groups and our final result to return.

The time complexity of this solution is ```O(n * m)```, where n is a total number of input words in the strs array, and m is the average length of a word in strs, because we iterate through and count occurencies of each character in the string.

### Java Solution:
````
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> res = new ArrayList<>();

        if(strs.length == 0){
            return res;
        }

        Map<String, List<String>> map = new HashMap<>();

        for(String word: strs){
            int[] count = new int[26];

            for(char c : word.toCharArray()){
                
                count[c - 'a']++;

            }
 
            String key = new String(Arrays.toString(count));

            if(map.containsKey(key)){
                map.get(key).add(word);
            }else{
                List<String> newArr = new ArrayList<>();
                newArr.add(word);
                map.put(key, newArr);
            }
        }

        res.addAll(map.values());
        return res;
        
    }
}

````









