---
title: A nice direct sum decomposition
date: 2024-09-04 00:00:00 +0200
---
## Motivation
I've recently came upon an interesting problem in Axler's *Linear Algebra Done Right*:
> Given \\(\phi \in \mathcal{L}(V, \mathbb{F})\\) and \\(u \in V\\) not in \\(\text{null }\phi\\)
> show that \\(V = \text{null }\phi \oplus \\{au | a \in \mathbb{F}\\}\\).

The proof is quite straightforward.
Since \\(\phi u \neq 0\\), \\(\phi u = c \in \mathbb{F}\\) is a basis of \\(\mathbb{F}\\) (notice that now we're talking about \\(\mathbb{F}\\) as vector space, not a field).
So, for any \\(v \in V\\), we have that \\(\phi v = bc = b \phi u = \phi (bu)\\) for some \\(b \in \mathbb{F}\\).
Thus, \\(0 = \phi v - \phi (bu) = \phi(b - bu)\\) which means that \\(v - bu = v_{\text{null}} \in \text{null } \phi\\).

This proves that \\(v \in \text{null }\phi + \\{au | a \in \mathbb{F}\\}\\).
Moreover, if \\(v_\text{null} + au = 0\\) for some \\(v_\text{null} \in \text{null }\phi\\), then \\(\phi(v_\text{null} + au) = a\phi u = ac = 0\\), so \\(a = 0\\) and \\(v_\text{null} = 0\\), meaning that we have a direct sum.

It's a known fact that for any given subspace \\(U\\) of a finite-dimensional space \\(V\\), it is always possible to find a subspace \\(W\\) such that \\(V = U \oplus W\\) (in some sense this subspace is *complementary* to \\(U\\)).
Hence, it must be possible to find a subspace complementary to \\(\text{null } T\\) for any linear map.
This proof above can be generalized to any one-dimensional space, i.e. to a map in \\(\mathcal{L}(V, W)\\), where \\(\text{dim } W = 1\\).
It is not clear however how to complement the null space in other cases.
So here I'll show one way of doing that.
The decomposition we get as a result, can be applied to another problem which I'll also discuss.

## The decomposition
Assume that \\(W\\) is finite-dimensional, and we have a linear map \\(T \in \mathcal{L}(V, W)\\).
Since \\(W\\) is finite-dimensional, \\(\text{range } T\\) is also finite-dimensional.
Let \\(w_1, \dots, w_n\\) be the basis of \\(\text{range }T\\).
There are also some \\(v_i \in V\\) such that \\(Tv_i = w_i\\).

With this setup out of the way, we can state the fact that's the highlight of this post:
\\[V = \text{null }T \oplus \text{span}(v_1, \dots, v_n).\\]
Let's look at the proof (in essence very similar to the one we've seen before).

For any \\(v \in V\\), we have that [\\(i\\) is the summation index]
\\[Tv = \sum a_i w_i = \sum a_i T v_i = T\left( \sum a_i v_i \right).\\]
This implies that
\\[0 = Tv - T\left( \sum a_iv_i \right) = T \left( v - \sum a_i v_i \right).\\]
Hence,
\\[v - \sum a_i v_i \in \text{null }T,\\]
so \\(v = v_\text{null} + \sum a_i v_i\\), for some \\(v_\text{null} \in \text{null }T\\);
in other words, \\(v \in \text{null }T + \text{span}(v_1, \dots, v_n)\\).

To show that this is a direct sum, suppose that \\(v_\text{null} + \sum a_i v_i = 0\\).
Applying \\(T\\) to both sides gives
\\[T(v_\text{null} + \sum a_i v_i) = 0,\\]
which implies (by linearlity of \\(T\\)) that
\\[\sum a_i T v_i = \sum a_i w_i = 0.\\]
Since \\(w_1, \dots w_n\\) is linearly independent, for all \\(i\\), \\(a_i = 0\\).
This means that the "span element" is \\(0\\) and so is \\(v_\text{null}\\), so this is indeed a direct sum.

## Application
This decomposition can be used to prove the following statement:
> Assume that \\(W\\) is finite dimensional, and \\(T_1, T_2 \in \mathcal{L}(V, W)\\),
> then \\(\text{null }T_1 = \text{null }T_2\\) if and only if there exists an invertible \\(S \in \mathcal{L}(W)\\) such that \\(T_1 = ST_2\\).

The "if" part is very easy to prove: let \\(v \in \text{null }T_1\\), then \\(0 = T_1v = (ST_2)v = S(T_2v)\\).
Since \\(S\\) is injective, \\(\text{null }S = \\{0\\}\\), so \\(T_2v = 0\\), showing that \\(v \in \text{null }T_2\\).
The proof for the inclusion \\(\text{null }T_2 \subseteq \text{null }T_1\\) is completely analogous.

Now for the juicy part.

Just as in the proof for the direct sum decomposition, we let \\(w_1, \dots, w_n\\) be the basis of \\(\text{range }T_1\\) and \\(v_i \in V\\) be such that \\(T_1v_i = w_i\\).
It's not hard to prove that \\(T_2v_1, \dots, T_2v_n\\) is linearly independent.
Indeed, from the assumption that there are some \\(a_i\\)'s such that \\(\sum a_i T_2 v_i = T_2 \left( \sum a_i v_i \right) = 0\\), we get that \\(\sum a_i v_i \in \text{null }T_2 = \text{null }T_1\\), so 
\\[\sum a_i v_i \in \text{null } T_1 \cap \text{span}(v_1, \dots, v_n) = \\{0\\}.\\]
Hence, \\(\sum a_i v_i = 0\\) which implies that \\(T_1 \left( \sum a_i v_i \right) = \sum a_i w_i = 0\\).
Now, linear independence of \\(w_i\\)'s forces each \\(a_i\\) to be \\(0\\) (by the way, as a byproduct we get that \\(v_i\\)'s are also linearly independent).

Since \\(T_2v_1, \dots, T_2v_n\\) is linearly independent in \\(W\\), it can be extended to a basis of \\(W\\) as
\\(T_2v_1, \dots, T_2v_n, e_1, \dots, e_k\\).
As another basis of \\(W\\) we have \\(w_1, \dots, w_n, f_1, \dots, f_k\\).
We can define \\(S \in \mathcal{L}(W)\\) in the following way:
\\[S(T_2v_i) = w_i \text{ and } Se_i = f_i.\\]
Now, for any \\(v \in V\\), using our decomposition we have that \\(v = v_\text{null} + \sum a_i v_i\\), and
\\[(ST_2)v = S\left(T_2\left( v_\text{null} + \sum a_i v_i\right)\right) = S \left( \sum a_i T_2 v_i \right) = \sum a_i S(T_2 v_i) = \sum a_i S(T_2 v_i).\\]
Using the definition of \\(S\\), the sum above is equal to
\\[\sum a_i w_i = \sum a_i T_1 v_i = T_1 \left( \sum a_i v_i \right) = T_1\left(v_\text{null} + \sum a_i v_i \right) = T_1v.\\]

This proves that \\(ST_2 = T_1\\).
All we have to do now is show that \\(S\\) is invertible.

For that we need a short lemma:
> If \\(V = \text{span}(v_1, \dots, v_n), T \in \mathcal{L}(V, W)\\),
> then \\(\text{span}(Tv_1, \dots, Tv_n) = \text{range }T\\).

For \\(w \in \text{span}(Tv_1, \dots, Tv_n)\\), \\(w = \sum a_i Tv_i = T\left(\sum a_i v_i\right)\\), so \\(w \in \text{range }T\\). \\
For \\(w \in \text{range }T\\), there exists \\(v \in V\\) such that \\(w = Tv\\), and \\(v = \sum a_i v_i\\) for some \\(a_i\\)'s.
So \\(w = T\left( \sum a_i v_i \right) = \sum a_i T v_i \in \text{span}(Tv_1, \dots, Tv_n)\\).

Back to the invertibility argument.
Since \\(W = \text{span}(T_2v_1, \dots, T_2v_n, e_1, \dots e_k)\\), using the lemma above we get
\\[\text{span}(S(T_2v_1), \dots S(T_2v_n), Se_1, \dots, Se_k) = \text{span}(w_1, \dots, w_n, f_1, \dots, f_k) = \text{range }S.\\]
This proves that \\(W = \text{range }S\\), i.e. that \\(S\\) is surjective, and since \\(S\\) is an operator, this equivalent to \\(S\\) being invertible.