---
layout: post
title:  "Inverting a Binary Tree in Scala and C++"
date:   2020-12-16 15:24 +0000
---
I don't intend to apply to Google any time soon, but I'm buzzed on coffee and felt like doing a simple exercise in a language I'm familiar with and enjoy (Scala), and a language I'm less familiar with but still enjoy and is probably going to get me more jobs or PhDs (C++).

## Binary trees
![A binary tree](/assets/binary_tree.JPG)
A *binary tree* is a tree in which each node has at most has at most two children (a bifurcating arborescence), called the *left* child and *right* child. Inverting a binary tree is a common and memeified interview question, where the left child of each node is swapped with the right child. A binary tree is *full* if each node has precisely zero or two children.

The easiest (best? only?) algorithm for inverting a binary tree is recursive: replace the left child of the root with the inverted right child, and vice versa. In the worst case scenario, inverting takes time on the order of 2<sup>*d*</sup>, where *d* is the depth of the tree. Indeed, if *T(d)* is this time, then *T(1) = C<sub>1</sub>* (there is nothing to do), and *T(d) = C<sub>2</sub> + 2 T(d-1)* otherwise.

Is there a better algorithm? Doubtful.

## Scala
Using [Scalaz's](https://scalaz.github.io/7/) `Maybe` monad, we can define a binary tree to be 
{% highlight scala %}
final case class BinaryTree[A](value: A, left: Maybe[BinaryTree[A]], right: Maybe[BinaryTree[A]])
{% endhighlight %}

In the companion object of `BinaryTree`, we define the `invert` function by
{% highlight scala %}
def invert(tree: BinaryTree[A]): BinaryTree[A] = {
  val left = for {
    oldLeft <- tree.left
  } yield invert(oldLeft)

  val right = for {
    oldRight <- tree.right
  } yield invert(oldRight)

  BinaryTree[A](tree.value, right, left)
}
{% endhighlight %}
The for-comprehensions here are sugaring `Maybe#map`, allowing us to grab the child binary tree if it exists, and short-circuiting to `Maybe.Empty` if it doesn't.

We can also define a full binary tree to be a coproduct given by
{% highlight scala %}
sealed abstract class FullBinaryTree[A]
final case class Branch[A](value: A, left: FullBinaryTree[A], right: FullBinaryTree[A]) extends FullBinaryTree[A]
final case class Leaf[A](value: A) extends FullBinaryTree[A]
{% endhighlight %}

Inverting a full binary tree becomes a sexy pattern-match with this definition. In the companion object of `FullBinaryTree`, we define
{% highlight scala %}
def invert[A](tree: FullBinaryTree[A]): FullBinaryTree[A] = tree match {
  case leaf: Leaf[A]              => leaf
  case Branch(value, left, right) => Branch(value, invert(right), invert(left))
}
{% endhighlight %}

What we might like to do to please any object-oriented programmers is then, in a separate `syntax` package, provide extensions to `BinaryTree` and `FullBinaryTree` as in 
{% highlight scala %}
implicit class BinaryTreeOps[A](tree: BinaryTree[A]) {
  def invert: BinaryTree[A] = BinaryTree.invert(tree)
}

implicit class FullBinaryTreeOps[A](tree: FullBinaryTree[A]) {
  def invert: FullBinaryTree[A] = FullBinaryTree.invert(tree)
}
{% endhighlight %}
This is a pattern I've become quite fond of in Scala, since it decouples data, implementation, and interface, providing an entry point for a DSL to take over the `syntax` package without touching the actual `BinaryTree` classes and objects. Anybody who actually works in the industry might throw up at this for a couple of reasons: the extensions involve an allocation which is a pointless waste of resources, and separating data and functionality is antithetical to the concept of OOP. That being said, I don't work in the industry so neither of these things are an issue to me, so long as the code is pretty. Maybe somebody created an OOP pattern somewhere down the line and called it the three-layer gateau or something.

## C++
With our C++ binary tree, we have to think about memory and templates and header files. Templates aren't fond of the C++ header-import system, so I just implemented all the functions I need in the header file. For the exposition, I'll ignore this limitation and pretend I can put things in the corresponding source file.

We define our binary tree class to be 
{% highlight c++ %}
template <typename T>
class BinaryTree {
private:
    T value;
    BinaryTree<T> const* left;
    BinaryTree<T> const* right;

public:
    BinaryTree(T value, BinaryTree<T> const* left, BinaryTree<T> const* right);
    ~BinaryTree();

    static BinaryTree<T> const* invert(BinaryTree<T> const* tree);
};
{% endhighlight %}
The constructor and destructor are obvious: copy the given constructor parameters into the relevant fields; delete the left and right children.

For the invert function, we pass a (const) pointer rather than a (const) reference to facilitate a recursive definition. There's probably a better way to do this. The implementation is very easy and less abstract nonsense than the Scala version
{% highlight c++ %}
template <typename T>
static BinaryTree<T> const* BinaryTree<T>::invert(BinaryTree<T> const* tree) {
    if (tree == nullptr) {
        return nullptr;
    }

    return new BinaryTree<T>(tree->value, invert(tree->right), invert(tree->left));
}
{% endhighlight %}
Returning a pointer to some dynamically-allocated tree is a horrible idea and invites a naive caller to cause a memory leak. It would be better to restrict this implementation to be a private method, and publicly expose the following instead, unless I'm being dumb.
{% highlight c++ %}
static BinaryTree<T> invert(BinaryTree<T> const& tree) {
    BinaryTree<T> invertedBinaryTree(tree.value, invert(tree.right), invert(tree.left));

    return invertedBinaryTree;
}
{% endhighlight %}
This way, as far as I know, the returned tree is allocated on the stack, and thanks to our destructor, its children will be destroyed when the tree goes out of scope. This avoids the problem of the caller having to manually delete a tree. A further benefit of this approach is being able to pass a reference instead, since the recursiveness is in our private implementation.
