# Segment Tree
```python
class SegmentTree:
    def __init__(self, arr):
        self.n = len(arr)
        self.tree = [0] * (4 * self.n)  # Tree array, typically 4*n size
        self.arr = arr
        self._build(0, 0, self.n - 1)

    def _build(self, tree_idx, start, end):
        """
        Recursively builds the segment tree.
        tree_idx: Current index in the self.tree array.
        start: Starting index of the current segment in the original array.
        end: Ending index of the current segment in the original array.
        """
        if start == end:
            # Leaf node: stores the value from the original array
            self.tree[tree_idx] = self.arr[start]
            return

        mid = (start + end) // 2
        left_child = 2 * tree_idx + 1
        right_child = 2 * tree_idx + 2

        # Recursively build left and right children
        self._build(left_child, start, mid)
        self._build(right_child, mid + 1, end)

        # Merge results from children (e.g., sum, min, max)
        # For sum query, it's the sum of its children
        self.tree[tree_idx] = self.tree[left_child] + self.tree[right_child]

    def query(self, query_start, query_end):
        """
        Queries the segment tree for a range [query_start, query_end].
        """
        return self._query(0, 0, self.n - 1, query_start, query_end)

    def _query(self, tree_idx, start, end, query_start, query_end):
        """
        Helper function for range query.
        tree_idx: Current index in the self.tree array.
        start: Starting index of the current segment in the original array.
        end: Ending index of the current segment in the original array.
        query_start: Start of the query range.
        query_end: End of the query range.
        """
        # Case 1: Current segment is completely outside the query range
        if query_start > end or query_end < start:
            return 0  # Return identity element (e.g., 0 for sum, infinity for min)

        # Case 2: Current segment is completely inside the query range
        if query_start <= start and end <= query_end:
            return self.tree[tree_idx]

        # Case 3: Current segment partially overlaps with the query range
        mid = (start + end) // 2
        left_child = 2 * tree_idx + 1
        right_child = 2 * tree_idx + 2

        # Recursively query left and right children
        left_sum = self._query(left_child, start, mid, query_start, query_end)
        right_sum = self._query(right_child, mid + 1, end, query_start, query_end)

        # Combine results (e.g., sum of left and right query results)
        return left_sum + right_sum

    def update(self, idx, new_val):
        """
        Updates the value at a specific index in the original array and propagates changes
        up the segment tree.
        idx: Index of the element to update in the original array.
        new_val: The new value for the element.
        """
        self._update(0, 0, self.n - 1, idx, new_val)
        self.arr[idx] = new_val  # Also update the original array

    def _update(self, tree_idx, start, end, idx, new_val):
        """
        Helper function for update operation.
        tree_idx: Current index in the self.tree array.
        start: Starting index of the current segment in the original array.
        end: Ending index of the current segment in the original array.
        idx: Index of the element to update.
        new_val: The new value for the element.
        """
        # Base case: Leaf node corresponding to the updated index
        if start == end:
            self.tree[tree_idx] = new_val
            return

        mid = (start + end) // 2
        left_child = 2 * tree_idx + 1
        right_child = 2 * tree_idx + 2

        # Decide whether to go left or right based on the index to update
        if start <= idx <= mid:
            self._update(left_child, start, mid, idx, new_val)
        else:
            self._update(right_child, mid + 1, end, idx, new_val)

        # After updating the child, update the current node
        self.tree[tree_idx] = self.tree[left_child] + self.tree[right_child]


# Example Usage:
if __name__ == "__main__":
    my_array = [1, 3, 5, 7, 9, 11]
    segment_tree = SegmentTree(my_array)

    print("Original array:", my_array)
    print("Segment Tree (internal representation, first few elements):", segment_tree.tree[:15]) # Print a few elements as it's often sparse

    # Query sum of a range
    print("\nQuerying sum of range [1, 4]:")  # Should be 3 + 5 + 7 + 9 = 24
    print("Sum:", segment_tree.query(1, 4))

    print("\nQuerying sum of range [0, 2]:")  # Should be 1 + 3 + 5 = 9
    print("Sum:", segment_tree.query(0, 2))

    print("\nQuerying sum of range [3, 5]:")  # Should be 7 + 9 + 11 = 27
    print("Sum:", segment_tree.query(3, 5))

    # Update an element
    print("\nUpdating element at index 2 from 5 to 10.")
    segment_tree.update(2, 10)
    print("Updated array:", segment_tree.arr)
    print("Segment Tree (internal representation, first few elements):", segment_tree.tree[:15])

    # Query after update
    print("\nQuerying sum of range [1, 4] after update:") # Should be 3 + 10 + 7 + 9 = 29
    print("Sum:", segment_tree.query(1, 4))

    print("\nQuerying sum of range [0, 2] after update:") # Should be 1 + 3 + 10 = 14
    print("Sum:", segment_tree.query(0, 2))
```
