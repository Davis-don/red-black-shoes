# Red-Black Trees

A **Red-Black Tree** is a self-balancing binary search tree (BST) where each node contains an additional bit for storing the color of the node, either **red** or **black**. Red-Black Trees ensure that the tree remains balanced during insertions and deletions, which guarantees that the operations on the tree are efficient.

## Properties of Red-Black Trees

A Red-Black Tree must satisfy the following properties:

1. **Node Color Property**:
   - Each node is either **red** or **black**.

2. **Root Property**:
   - The root node is always **black**.

3. **Leaf Property**:
   - Every **leaf node** (NULL or NILL node) is black.

4. **Red Property**:
   - If a red node has children, then the children must be black. In other words, two red nodes cannot be adjacent (i.e., there cannot be two consecutive red nodes in a path).

5. **Black Height Property**:
   - Every path from a node to its descendant NULL node must have the same number of black nodes. This number is referred to as the **black height** of the tree.

6. **Balanced Property**:
   - No path from the root to any leaf (or NULL) can be more than twice as long as any other path. This ensures that the tree remains balanced.

## Operations on Red-Black Trees

### 1. Insertion

The insertion process involves inserting a new node as a red node and then ensuring that the Red-Black properties are maintained. The following steps are followed for insertion:

1. Insert the node in the same way as a regular binary search tree (BST), as a red node.
2. Fix any violations of the Red-Black properties using rotations and color changes.

   - **Case 1**: The inserted node's uncle is red (both parent and uncle are red).
     - Recolor the parent and uncle to black, and the grandparent to red.
     - Move the current node up to the grandparent.
   
   - **Case 2**: The inserted node's uncle is black and the node is on the **outside** (i.e., the "Zig-Zag" case).
     - Perform a rotation (either left or right) to convert it into the inside case.
   
   - **Case 3**: The inserted node's uncle is black and the node is on the **inside** (i.e., the "Zig-Zig" case).
     - Perform a single rotation to restore balance.

3. If necessary, rotate the tree to restore the balance and ensure that the root remains black.

### 2. Deletion

The deletion process involves removing a node and then ensuring that the Red-Black properties are maintained. The steps are:

1. **Remove the node**: First, perform the regular BST deletion process to remove the node.
   
2. **Fix violations**: After removal, if the deleted node or its child is black, the Red-Black properties could be violated. To fix this:
   
   - **Case 1**: The sibling is red.
     - Perform a rotation to move the red sibling up and the parent down.
   
   - **Case 2**: The sibling is black and both its children are black.
     - Recolor the sibling to red and move up the fix.
   
   - **Case 3**: The sibling is black, and one of its children is red.
     - Perform a rotation and recoloring to restore balance.

3. After the fix, the root should always be black.

### 3. Rotations

Rotations are used to maintain the balance of the tree. There are two types of rotations:

- **Left Rotation**: A left rotation is used to move a node down the tree and its right child up.
- **Right Rotation**: A right rotation is used to move a node down the tree and its left child up.

These rotations help to restructure the tree when necessary to preserve the Red-Black properties.

### Time Complexity

The time complexity for the following operations in a Red-Black Tree is **O(log n)**:
- **Insertion**
- **Deletion**
- **Search**

This is because the height of the tree is guaranteed to be **O(log n)**, where `n` is the number of nodes in the tree. The balancing operations (rotations and color changes) can be done in constant time, which ensures that these operations remain efficient.

## Example

Below is an example of how nodes are inserted into a Red-Black Tree:

1. **Insert 10**: The tree will have a single black node, as it is the root.
   
2. **Insert 20**: The node is inserted as a red node. Since no Red-Black properties are violated, the tree remains balanced.

3. **Insert 30**: After inserting, the tree will need to perform a rotation to restore balance, as it will have two consecutive red nodes.

This is a high-level overview of how Red-Black Trees operate. By maintaining these properties, Red-Black Trees ensure efficient search, insertion, and deletion operations.
