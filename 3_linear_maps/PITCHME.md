{{{PURPLESLIDE}}}

## Linear maps

COMP1021 MCS: Linear algebra

---

## Previously

See the [concept diagram](https://github.com/stevenaeola/linalg_lectures/blob/d8f9499b9cf54ca5a070822454ac384ae93ce659/concepts.mmd)

Things in pink we will look at today (and next time)

---

## Questions

{{{APPEAR}}}

- From the practicals last week?
- From <https://pollev.com/stevenaeola>

---
{{{APPEAR}}}

## Basis representation

- Remember: a set of vectors is a __basis__ for the vector space if it __spans__ the whole space and is __linearly independent__

- __Thm__ For a vector space $V$ the representation of any $\mathbf{v} \in V$ as a linear combination of a given basis $S = \lbrace \mathbf{s}_1,\ldots,\mathbf{s}_n \rbrace$ is unique
- __Proof__ (sketch). Suppose not. Then subtract the two representations. This violates one of the properties of a basis. So we have a contradiction.

---

## Canonical (standard) basis

- This is kind of obvious for the _canonical basis_ for $\Bbb{R}^n$ 
$$\lbrace \mathbf{e}_i: i \leq 1 \leq n \rbrace$$
- Where $\mathbf{e}_i$ is the vector with a 1 in the ith position and 0 elsewhere
- In 3D sometimes referred to as $\mathbf{e}_x,\mathbf{e}_y,\mathbf{e}_z$ or $\mathbf{i},\mathbf{j},\mathbf{k}$



---

{{{APPEAR}}}

## Linear map

__Defn__ If we have a function $f:V \rightarrow W$ where $V$ and $W$ are vectors spaces over a field $F$ then $f$ is a _linear map_ if for any vectors $\mathbf{u}, \mathbf{v} \in V$ and $a \in F$
$$f(\mathbf{u} + \mathbf{v}) = f(\mathbf{u}) + f(\mathbf{v})$$
$$f(a \mathbf{v}) = a f(\mathbf{v}) $$

---

- This means that a linear map _respects_ linear combinations
- Linear maps are sometimes called _linear transformations_ or _vector space homomorphisms_
- If $V=W$ then $f$ is an _endomorphism_
- All linear maps preserve lines

---

{{{APPEAR}}}

## Examples of linear maps

- Scaling (on $\Bbb{R}^3$)
- Reflection
- Rotation
- Shearing 
- Projection
- Embedding
- Differentiation (on polynomials)

---

## Linear maps and basis vectors

- Every vector $\mathbf{v}$ can be represented as a linear combination of basis vectors $\mathbf{s}_i \in S$
- If we apply a linear map $f$ then

`$$f(\mathbf{v}) = f(\sum_{i=1}^n a_i \mathbf{s}_i) = \sum_{i=1}^n a_i f(\mathbf{s}_i)$$`

- So a _linear map is characterised by its action on basis vectors_

---

{{{APPEAR}}}

## Images of basis vectors

For example, rotation by 90 degrees anti-clockwise in $\Bbb{R}^2$
- Q: What are the images of the canonical basis vectors $\mathbf{e}_1 (1,0)$ and $\mathbf{e}_2 (0,1)$?
- A: $(0,1)$ and $(-1,0)$ or $\mathbf{e}_2$ and $-1\mathbf{e}_1$
- Turn these into column vectors to get the  matrix representation

`$$\begin{pmatrix}0&-1 \\1 & 0 \end{pmatrix}$$`

---

## You try

Choose one of the linear map examples

Write down the images of the basis vectors in either $\Bbb{R}^2$ or $\Bbb{R}^3$

---

## Calculating from basis vector images

What happens when we rotate the vector $(2,3)$?

`$$\begin{aligned} rotate((2,3)) &= rotate(2\mathbf{e}_1 + 3\mathbf{e}_2) \\
&= 2.rotate(\mathbf{e}_1) + 3.rotate(\mathbf{e}_2)\\
&= 2\mathbf{e}_2 + 3.(-1.\mathbf{e}_1) \\
&= (-3,2)
\end{aligned}$$`

---

## Generalising basis images

Write basis vector images columns under f as a matrix

`$$\small{ A = \begin{pmatrix} a_{11} & a_{12} & \ldots & a_{1n}\\a_{21} & a_{22} & \ldots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots \\a_{m1} & a_{m2} & \ldots & a_{mn}
\end{pmatrix}}$$`

$a_{ij}$ is ith component of f-image of jth basis vector

$$f(\mathbf{e_j}) = \sum_{i=1}^m a_{ij} \mathbf{e}_i$$

---

The image of the vector $A\mathbf{x} = A(x_1,\ldots,x_n)$ is

`$$\small{\begin{aligned}
f(\sum_{j=1}^n x_j\mathbf{e}_j) &= \sum_{j=1}^n x_j f(\mathbf{e}_j) \\
&= \sum_{j=1}^n x_j \sum_{i=1}^m a_{ij} \mathbf{e}_i \\
&= \sum_{j=1}^n \sum_{i=1}^m a_{ij} x_j \mathbf{e}_i \\
\end{aligned}}$$`

So the ith component of the image of $\mathbf{x}$ is $$\sum_{j=1}^m a_{ij} x_j$$

---

## Example

`$$\begin{pmatrix} 1 & -2 & 3 \\ -4 & 5 & -6 \end{pmatrix}
\begin{pmatrix} 9 \\ 8 \\7 \end{pmatrix} = 
\begin{pmatrix} 1 \times 9 -2 \times 8 + 3 \times 7 \\ -4 \times 9 +5 \times 8 -6 \times 7\end{pmatrix} =
\begin{pmatrix} 14 \\ -38\end{pmatrix}
$$`

What are the dimensions of the domain and codomain?

---

## Identity matrix

What is the matrix representation of the identity map?

All basis vectors map to themselves via the identity matrix $I$

`$$\small{ I = \begin{pmatrix} 1 & 0 & \ldots & 0 \\ 0 & 1 & \ldots & 0\\
\vdots & \vdots & \ddots & \vdots \\0 & 0 & \ldots & 1
\end{pmatrix}}$$`

$I$ is a _diagonal_ matrix: $i \neq j \implies a_{ij}=0$
---

{{{APPEAR}}}

## Combining linear maps

- Suppose we have two linear maps $f$ and $g$ represented by matrices $A$ and $B$
- What is the matrix for $(f \circ g)(\mathbf{v}) = f(g(\mathbf{v}))$?
- Need to find images of basis vectors
- $B$ columns contains images of basis vectors under $g$
- So apply $A$ to columns of $B$ in turn and write as columns
- This gives the matrix of the map $f \circ g$ which we write $AB$

---

## Matrix multiplication

Given matrices $A \in \Bbb{R}^{m \times n}$ and $B \in \Bbb{R}^{n \times k}$

The elements $c_{ij}$ of the product $C = AB \in \Bbb{R}^{m \times k}$ are

$$c_{ij} = \sum_{l=1}^{n} a_{il}b_{lj}$$

For $1 \leq i \leq m, 1 \leq j \leq k$

This also formalises our definition of multiplying a matrix by a vector $k=1$

---

## Example

`$$\begin{pmatrix} 1 & 2 & 3 \\ 3 & 2 & 1 \end{pmatrix}
\begin{pmatrix} 0 & 2 \\ 1 & -1 \\ 0 & 1 \end{pmatrix}$$`

Check your answer example 2.3 from [MML book](https://mml-book.github.io/book/mml-book.pdf)

---

{{{BLUESLIDE}}}

## More

- [3B1B Chapter 3: Linear transformations and matrices](https://www.youtube.com/watch?v=kYB8IZa5AuE&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=3) 
- [3B1B Chapter 4: Matrix multiplication as composition](https://www.youtube.com/watch?v=XkY2DOUCWMU&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=4)
- [MML book](https://mml-book.github.io/book/mml-book.pdf) section 2.2

Next time: Determinants and inverses

Practicals: Span, independence, basis, linear maps, matrices