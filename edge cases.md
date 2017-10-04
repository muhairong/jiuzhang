1. Insert
  - LRU Cache (http://www.lintcode.com/en/problem/lru-cache/)
  - when insert a node, remember to check if this node is already exists, update or delete the old one
  - check node's existence must do first, if you check size first, you might delete node by mistake
  - after check it, check the size, if more than capacity, remove head node
