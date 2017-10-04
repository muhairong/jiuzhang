1. Insert
  - existence
    - LRU Cache (http://www.lintcode.com/en/problem/lru-cache/)
    - when insert a node, remember to check if this node is already exists, update or delete the old one
    - check node's existence must do first, if you check size first, you might delete node by mistake
    - after check it, check the size, if more than capacity, remove head node
  - overflow
    - (http://www.lintcode.com/en/problem/ugly-number-ii/)
    - when using multiplication, check the answer less than the type maximum number

2. vector.back()
  - (http://www.lintcode.com/en/problem/ugly-number-ii/)
  - when compare with v.back(), you must check whether the vector is empty first
