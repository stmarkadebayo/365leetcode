[Question](https://leetcode.com/problems/container-with-most-water/)

### My Approach
---------------------
The most a container can hold is limited by the shortest wall. So we consider an approach with max width and the shortest wall.

One pointer at the beginning (left), and the other at the very end (right), it gives the max possible width, then we calculate the area = width * shortest wall. Then to find a better area, we move the shorter wall (pointer) with the chance of finding a taller wall that makes up for loss in width. Repeat whilst keeping track of the biggest area so far.

### Implementation
-------------------------------
```python
class Solution:
    def maxArea(self, height):
        left = 0
        right = len(height) - 1
        max_water = 0

        while left < right:
            # calculate the width between the two walls
            width = right - left

            # the water level is limited by the shorter wall
            current_height = min(height[left], height[right])

            # update max_water if the current container is bigger
            max_water = max(max_water, width * current_height)

            # we then move the shorter wall because moving the taller one
            # would never result in more water.
            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_water
```

### Complexities
---------------------------------
- **Time: O(n)** — We traverse through the array once with two pointers moving towards each other
- **Space: O(1)** — Only using constant extra space with a few variables