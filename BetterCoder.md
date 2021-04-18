# 关于学算法的⼀些经验

##  作为⼀个⼩⽩，算法该如何学习？

 对于算法的学习，我也是从⼀个⼩⽩⼀步步⾛来，当然，现在仍然很菜，，，不过，鉴于我觉得还有⼀ 些⼈⽐我更菜了，我决定谈谈我算法学习过程⾛过的坑，以及⾃⼰总结的⼀些经验，之前也有写过⼀篇 类似的，那时粉丝才⼏千，这篇算是修正版。 

#### 切勿盲⽬刷题：刷题前的知识积累

说实话，想要提⾼⾃⼰的算法，真的没啥捷径，我觉得最好的捷径就是脚踏实地着多动⼿去刷题，多刷题。

 但是，我必须提醒的是，如果你是⼩⽩，也就是说，你连常⻅的数据结构，如链表、树以及常⻅的算法 思想，如递归、枚举、动态规划这些都没学过，那么，我不建议你盲⽬疯狂着去刷题的。

⽽是先去找本 书先去学习这些必要的知识，然后再去刷题。 因为，如果这些基础都不懂的话，估计⼀道题做了⼏个⼩时，然后看答案都看不懂，做题没有任何思路，这是很难受的。

久⽽久之，估计没啥动⼒了，我刚开始就是这样，⼀道题答案看⼀天，然⽽还是不⼤懂，什么回溯啊，暴⼒啊，还不知道是啥意思。

也就是说，假如你要去诸如 LeetCode 这些⽹站刷题，那么，你要先具备⼀定的基础，这些基础包括：

1、常⻅数据结构：链表、树(如⼆叉树)。（是的，链表和⼆叉树是重点，图这些可以先放着） 

2、常⻅算法思想：贪婪法、分治法、穷举法、动态规划，回溯法。（贪婪、穷举、分治是基础，动态 规划有难度，可以先放着） 

以上列出来的算是最基本的吧。就是说你刷题之前，要把这些过⼀遍再去刷题。如果你连这些最基本的 都不知道的话，那么你再刷题的过程中，会很难受的，思路也会相对⽐较少。 

总之，千万不要急，先把这些基本的过⼀遍，⼒求理解，再去刷题。

总结下： 提⾼数据结构与算法没啥捷径，最好的捷径就是多刷题。但是，刷题的前提是你要先学会⼀些基本的数 据结构与算法思想。

#### AC 不是⽬的，我们要追求完美

如何刷题？如何对待⼀道算法题？ 我觉得，在做题的时候，⼀定要追求完美，千万不要把⼀道题做出来之后，提交通过，哇，舒服！然后 就赶紧下⼀道。

然⽽，我认为这意义不⼤，因为⼀道题的解法太多了，有些解法态粗糙了，我们应该要寻找最优的⽅法。

算法能⼒的提升和做题的数量是有⼀定的关系，但并不是线性关系。

也就是说，在做题的时候，要⼒求⼀题多解，如果⾃⼰实在想不出来其他办法了，可以去看看别⼈是怎么做的，千万不要觉得模仿别⼈的 做法是件丢⼈的事。反正我就算作出了最优解，也会经常去看看⼤神的代码⻓啥样，有时候发现，⼤神果然是⼤神，代码好简洁！

我做题的时候，我⼀看到⼀道题，可能第⼀想法就是⽤很粗糙的⽅式做，因为很多题采⽤暴⼒法都会很 容易做，就是时间复杂度很⾼。之后，我就会慢慢思考，看看有没其他⽅法来降低时间复杂度或空间复 杂度，例如是否可以状态保存，剪纸，是否可以采⽤动规等等。最后，我会去看⼀下别⼈的做法，当然，并不是每道题都会这样执⾏。就是看到有意思的题目会下意识的去思考有没有更好的结题方法。

衡量⼀道算法题的好坏⽆⾮就是时间复杂度和空间复杂度，所以我们要⼒求完美，就要把这两个降到最 低，令他们相辅相成。

举道例题吧（举了⽆数次了，哈哈）： 

**问题： ⼀只⻘蛙⼀次可以跳上 1 级台阶，也可以跳上 2 级。求该⻘蛙跳上⼀个 n 级的台阶总共有多少种跳 法？**

**⽅法1：：暴⼒递归** 

这道题不难，或许你会采取下⾯的做法：

```c++
int solve(int n) {
    if (n <=2) {
        return n;
    } else {
        return solve(n-1) + solve(n-2);
    }
}
```

这种做法的时间复杂度很⾼，指数级别了。但是如果你提交之后侥幸通过了，然后你就接着下⼀道题 了，那么你就要好好想想了。

**⽅法⼆：空间换时间** 

⼒求完美，我们可以考虑⽤空间换时间：这道题如何你去仔细想⼀想，会发现有很多是重复执⾏了。

不⾏你可以画个图

![](https://cdn.jsdelivr.net/gh/rongweihe/ImageHost01/gzh/fibbonaqie.png)

所以可以采取下⾯的⽅法：

```c++
// ⽤⼀个 HashMap 来保存已经计算过的状态
static std::map<int,int>mp;
int solve(int n) {
  if (n <= 2) {
    return n;
  } else {
    if (mp.count(n)) {
      return mp[n];
    } else {
      int m = solve(n-1) + solve(n-2);
      mp[n]=m;
      return m;
    }
  }
}
```

```java
static Map<Integer,Integer> map = new HashMap();
public static int solve(int n){
   if(n <= 2){
   		return n;
   } else {//是否计算过
   		if(map.containsKey(n)){
   			return map.get(n);
   		}else{
         int m = solve(n-1) + solve(n-2);
         map.put(n, m);
         return m;
   		}
 	}
}
```



# 链表刷题指南

## LeetCode-206.翻转链表

最简单的迭代法：

```c++
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* cur = nullptr, *pre = head;
        while (pre != nullptr) {
            ListNode* next = pre->next;
            pre->next = cur;
            cur = pre;
            pre = next;
        }
        return cur;
    }
};
```
