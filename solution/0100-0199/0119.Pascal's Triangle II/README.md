# [119. 杨辉三角 II](https://leetcode-cn.com/problems/pascals-triangle-ii)

[English Version](/solution/0100-0199/0119.Pascal%27s%20Triangle%20II/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>给定一个非负索引&nbsp;<em>k</em>，其中 <em>k</em>&nbsp;&le;&nbsp;33，返回杨辉三角的第 <em>k </em>行。</p>

<p><img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/0100-0199/0119.Pascal%27s%20Triangle%20II/images/PascalTriangleAnimated2.gif"></p>

<p><small>在杨辉三角中，每个数是它左上方和右上方的数的和。</small></p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> 3
<strong>输出:</strong> [1,3,3,1]
</pre>

<p><strong>进阶：</strong></p>

<p>你可以优化你的算法到 <em>O</em>(<em>k</em>) 空间复杂度吗？</p>


## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
class Solution:
    def getRow(self, rowIndex: int) -> List[int]:
        def makePascal(prevArr):
            if len(prevArr) == 0:
                return [1]
            elif len(prevArr) == 1:
                return [1, 1]
            else:
                NewArr = [0] * (len(prevArr) + 1)
                NewArr[0], NewArr[-1] = 1, 1
                for i in range(len(prevArr) - 1):
                    NewArr[i + 1] = prevArr[i] + prevArr[i + 1]
                return NewArr

        temp = []
        Pascal = []
        for i in range(rowIndex + 1):
            temp = makePascal(temp)
            Pascal.append(temp)
        return Pascal[rowIndex]
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> ret = new LinkedList<>();
        long nk = 1;
        for (int i = 0; i <= rowIndex; i++) {
            ret.add((int) nk);
            nk = nk * (rowIndex - i) / (i + 1);
        }
        return ret;
    }
}
```

### **Go**

```go
func getRow(rowIndex int) []int {
	row := make([]int, rowIndex+1)
	row[0] = 1
	for i := 1; i <= rowIndex; i++ {
		for j := i; j > 0; j-- {
			row[j] += row[j-1]
		}
	}
	return row
}
```

### **...**

```

```

<!-- tabs:end -->
