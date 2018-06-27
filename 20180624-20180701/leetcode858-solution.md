Note: If you prefer Chinese version, please visit this link. Don't forget to follow me on Zhihu as well.

I was praticing and found a interesting question. Here is the question:

![Alt text](pic/leetcode858.png?raw=true "Title")

Here is how I solve it:

# question analysis
if you are familiar with mirror reflection, you should know:

 Angle of incidence = Angle of reflection 
 
 so we can extend the mirror like this:
 ![Alt text](pic/leetcode858-1.png?raw=true "Title")
 
## example
 
 we can see that we simplify the problem by extending the 'mirror grid'. Then Let's see 2 case:
 
  ![Alt text](pic/leetcode858-2.png?raw=true "Title")
  
  Case A: Reflected twice. The receptor on bottom right accepted the ray. We can see that it was receptor 0
  
   Case B: Reflected 3 times. The receptor on upper right accepted the ray. We can see that it was receptor 2
  
  Let's define **k** as the bouncing time on the 'grid channel'(what I mean by channel here is the upper and lower bound of the grids).  From the example above, we can learn that :

## summary for the example
  
  1. if **k** is an odd number, then the ray will hit the receptor in bottom of the grid. But since there is only one receptor in the bottom, so we will return receptor 0 in this case
  2. if if **k** is an even number,then the ray will hit the receptor in upper bound of the grid. But since there are 2 receptors in the top, so we will analyze further then:
  
  	(1) The ray will only reach at the top right corner of the 'channel'. 
  	(2) we define **g_num** as the numbers of the grid when the ray reachs a receptor. we can learn from the examples that when **g_num** is odd, then last grid will be the same as the first grid. when **g_num** is even, the last grid will be a reflection of the first grid. We know that first grid is the original grid. In another word, if **g_num**  is odd, return receptor 1, else rturn receptor 2
  	(3) So how do we know what number **g_num** will be. It is simple. g_num = p * k / q. Why? Because ray had travelled **p * k** distance on Y direction, and q is the 'step', and only 1 step in every grid.
  	


#Coding
```python
class Solution(object):
    def mirrorReflection(self, p, q):
        """
        :type p: int
        :type q: int
        :rtype: int
        """
        k = 1  # uppper and lower bound bouncing time
        while k * p % q != 0:
            k += 1
        if k % 2 == 0:
            return 0
        else:
            g_num = p * k / q
            if g_num % 2 == 0:
                return 2
            else:
                return 1
```

69 / 69 test cases passed.
Status: Accepted
Runtime: 37 ms

#Conclusion
From this question, we can conclude that:

1. When you don't have idea about it, learn to find patttern from simple example
2. Every physical question to mathematical question.

