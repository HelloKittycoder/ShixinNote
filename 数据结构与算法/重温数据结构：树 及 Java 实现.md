[TOC]

数据结构，指的是数据的存储形式，常见的有线性结构（数组、链表，队列、栈），还有非线性结构（树、图等）。

今天我们来学习下数据结构中的 **树**。

##什么是树

线性结构中，一个节点至多只有一个头节点，至多只有一个尾节点，彼此连接起来是一条完整的线。

比如链表和数组：

![shixin tai shuai le](http://img.blog.csdn.net/20161111211817802)


而树，非线性结构的典型例子，**不再是一对一**，而变成了**一对多**（而图则可以是 多对多），如下图所示：

![shixin tai shuai le](http://img.blog.csdn.net/20161111212248502)


可以看到:

- 图中的结构就像一棵倒过来的树，最顶部的节点就是“**根节点 (root 节点)**”
- 每棵树**至多只有一个根节点**
- 根节点生出多个孩子节点，每个孩子节点**只有一个父节点**，每个孩子节点又生出多个孩子
- 父亲节点 (parent) 和孩子节点 (child) 是相对的
- 没有孩子节点的节点成为叶子节点 (leaf)

##树的相关术语

###根节点、父亲节点、孩子节点、叶子节点如上所述。

![shixinzhang](http://img.blog.csdn.net/20161112192748032)

###节点的度

一个节点**直接含有的子树个数**，叫做节点的度。比如上图中的 3 的度是 2，10 的度是 1。

###树的度

一棵树中 **最大节点的度**，即哪个节点的子节点最多，它的度就是 树的度。上图中树的度为 2 。

###节点的层次

从根节点开始算起，根节点算第一层，往后底层。比如上图中，3 的层次是 2，4 的层次是 4。

###树的高度

树的高度是从叶子节点开始，**自底向上增加**。

###树的深度

与高度相反，树的深度从根节点开始，**自顶向下增加**。

整个树的高度、深度是一样的，但是中间节点的高度 和 深度是不同的，比如上图中的 6 ，高度是 2 ，深度是 3。

##树的两种实现


从上述概念可以得知，树是一个递归的概念，从根节点开始，每个节点至多只有一个父节点，有多个子节点，每个子节点又是一棵树，以此递归。


树有两种实现方式：

- 数组
- 链表

###数组表示：

我们可以利用每个节点至多只有一个父节点这个特点，使用 **父节点表示法** 来实现一个节点：

	public class TreeNode {

    	private Object mData;   //存储的数据
    	private int mParent;   //父亲节点的下标

	    public TreeNode(Object data, int parent) {
	        mData = data;
	        mParent = parent;
	    }
	
	    public Object getData() {
	        return mData;
	    }
	
	    public void setData(Object data) {
	        mData = data;
	    }
	
	    public int getParent() {
	        return mParent;
	    }
	
	    public void setParent(int parent) {
	        mParent = parent;
	    }
	}

上述代码中，使用 角标 来指明父亲节点的位置，使用这个节点组成的数组就可以表示一棵树。

	public static void main(String[] args){
        TreeNode[] arrayTree = new TreeNode[10];
    }

用数组实现的树表示下面的树，（其中一种 ）结果就是这样的：


![shixinzhang](http://img.blog.csdn.net/20161112192748032)

![shixinzhang](http://img.blog.csdn.net/20161112223704256)


数组实现的树节点使用角标表示父亲的索引，下面用链表表示一个节点和一棵树：

###链表表示的节点：

	public class LinkedTreeNode {

	    private Object mData;   //存储的数据
	    private LinkedTreeNode mParent;   //父亲节点的下标
	    private LinkedTreeNode mChild;	//孩子节点的引用
	
	    public LinkedTreeNode(Object data, LinkedTreeNode parent) {
	        mData = data;
	        mParent = parent;
	    }
	
	    public Object getData() {
	        return mData;
	    }
	
	    public void setData(Object data) {
	        mData = data;
	    }
	
	    public Object getParent() {
	        return mParent;
	    }
	
	    public void setParent(LinkedTreeNode parent) {
	        mParent = parent;
	    }
	
	    public LinkedTreeNode getChild() {
	        return mChild;
	    }
	
	    public void setChild(LinkedTreeNode child) {
	        mChild = child;
	    }
	
	}

使用引用，而不是索引表示父亲与孩子节点。

使用一个 List, 元素是 LinkedTreeNode，就可以表示一棵链表树：

    public static void main(String[] args){
        LinkedList<LinkedTreeNode> linkedTree = new LinkedList<>();
    }

这样只需知道 根节点就可以遍历整个树。知道某个节点也可以获取它的父亲和孩子。

##树的几种常见分类及使用场景

树，为了更好的查找性能而生。

常见的树有以下几种分类：

- 二叉树
- 平衡二叉树
- B 树
- B+ 树
- 哈夫曼树
- 堆
- 红黑树

接下来陆续介绍。



