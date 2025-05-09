This post is meant to describe what SE3 equivariance is, why its important in modeling of molecules, and how it is achieved in neural netowrks. 

We begin by first describing the concepts of invariance and equivariance. We will first describe these two idea informally, and then later, more formally using the language of group theory. 

- Invariance: A function is invariant to certain types of changes (e.g. translation in Euclidean space) in its input if the output of he function remains the same even after the input is changed. 
- Equivariance: A function is said to be equivaraint to certain types of changes in its input if, after the application of such transformations to the input, the output of the function undergoes some predictable transofrmation. For example, a Euclidean translation in the input might produce a predictable euclidean translation in the output. 

The relevant papers are: 

- Group-Equivariance Convolutional Networks
- Tensor Field Networks
- SE3-Transformer: max welling at al., 2020


And now going into the details.

- Understanding this space properly requires delving just a little bit into group theory - understanding what a Group is and what a Lie Group is - just enough so that we can follow the language in the literature on 3D molecular modeling. These foundational concepts enable further exploration into more complex structures like SE(3)-equivariant models, which respect the symmetries of the 3-dimensional Euclidean space (involving both rotations and translations).

  - Group: A group is a mathematical concept that consists of a set of elements along with an operation (like addition or multiplication) that combines any two elements to form a third element. These elements can be numbers, matrices, rotations, etc., and the operation could be something like addition, multiplication, or a more abstract operation. This operation must satisfy four key conditions: 
    - Closure: If you take any two elements from the group and operate on them, the result must also be an element of the group.
    - Associativity: The order in which operations are performed does not affect the outcome (e.g., $(a * b) * c = a * (b * c)$).
    - Identity Element: There must be an element in the group that, when combined with any other element, results in the original element (e.g., $a * e = e * a = a$).
    - Inverse Element: For every element in the group, there must be another element that, when combined with it, results in the identity element (e.g., $a * a^-1 = a^-1 * a = e$).

  - Lie group: A Lie group is a special type of group that is also a differentiable manifold, meaning it has a structure that allows for calculus operations like differentiation. In simple terms, it's a group for which the elements and operations are smooth and continuous. This allows for the powerful combination of algebraic operations (from group theory) and calculus. Lie groups are particularly useful in physics and engineering because they can describe continuous symmetries and transformations such as rotations, translations, and scaling. They form the basis for much of modern physics, including the theory of relativity and quantum mechanics.

  - Symmetry: Symmetry refers to a situation where something does not change under a set of operations or transformations. In mathematics and physics, symmetry describes how an object or a system remains invariant (unchanged) under certain transformations such as rotations, reflections, or translations. For instance, a circle exhibits rotational symmetry because it looks the same after being rotated by any angle about its center. In the context of groups, a symmetry of an object can be described by the set of all transformations that leave the object unchanged, and this set can form a group. In 3D molecular modeling and computer vision, understanding these concepts helps in designing algorithms that are invariant to changes in orientation or position of molecules and objects, which is crucial for accurate modeling and recognition.

- Some nomenclature: 
  - O(3): Orthogonal group of degree 3, consists of all 3x3 orthogonal matrices with real entries. This includes all transfomations in 3D that preserve the length of the vectors, i.e. they include all rotations and reflections. The determinant of an orthogonal matrix can be either +1 or -1, where -1 corresponds to a reflection. 
  - SO(3): the Special Orthogonal group of degree 3 is a subgroup of O(3), that includes all 3 x 3 orthogonal matrices with determinant +1, but doesn't include matrices with determinant -1, i.e. refelctions. 
  - SE(3):  Special Euclidean group in three dimensions, is the group of rigid body transformations in 3D space. It combines rotations and translations, capturing the full set of possible movements that an object can undergo without changing its shape. Mathematically, an element of SE(3) can be represented as a combination of a rotation matrix $R$ from SO(3) and a translation vector $t$.  
  - E(3): Euclidean Group. the Euclidean group in three dimensions, generalizes SE(3) by including all isometries: transformations that preserve distances and angles in 3D space. This includes not only the rigid body transformations (rotations and translations) of SE(3) but also reflections and glide reflections. E(3) effectively captures all possible ways to move an object in space while preserving its geometry.
