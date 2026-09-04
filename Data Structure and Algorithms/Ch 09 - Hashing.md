# Chapter 9: Hashing

Hashing provides near‑constant‑time insertion, deletion, and lookup by mapping keys to array indices using a hash function. This chapter covers hash functions, collision resolution strategies, load factor, rehashing, implementations of hash maps and sets, and classic applications.

## 1. Hash Functions

**What**: A function that maps a key (integer, string, or any object) to an integer index within a fixed range `[0, m‑1]`.

**Desirable properties**:
- **Deterministic**: Same key always produces the same hash.
- **Fast to compute**: O(1) or O(len(key)).
- **Uniform distribution**: Minimises collisions by spreading keys evenly.
- **Minimises collisions**: Different keys should rarely map to the same index.

**Simple examples**:
- Integer keys: `hash(key) = key % m` (choose `m` as a prime number to improve distribution).
- String keys: polynomial rolling hash `hash = (hash * BASE + char) % m`.

```java
// Simple integer hash
int hashInt(int key, int m) { return key % m; }

// Polynomial rolling hash for strings
int hashString(String key, int m) {
    final int BASE = 31;
    long hash = 0;
    for (char c : key.toCharArray()) hash = (hash * BASE + c) % m;
    return (int)hash;
}
```

**Real-life analogy**: Library classification. A book’s title (key) is mapped to a shelf number (hash). Good classification distributes books evenly across shelves.

## 2. Collision Resolution

A collision occurs when two different keys hash to the same index.

### 2.1 Chaining (Separate Chaining)

**What**: Each bucket contains a linked list (or dynamic array) of key‑value pairs that hash to that bucket.

**Operations**:
- Insert: hash to bucket, add to list (check for duplicates if needed).
- Search: hash to bucket, traverse list.
- Delete: hash to bucket, remove from list.

**Performance**:
- Average: O(1 + α) where α = n/m (load factor).
- Worst case (all keys in one bucket): O(n).

class HashMapChaining<K, V> {
    static class Node<K, V> {
        K key;
        V value;
        Node<K, V> next;
        
        Node(K key, V value) {
            this.key = key;
            this.value = value;
            this.next = null;
        }
    }
    
    private Node<K, V>[] buckets;
    private int size;
    private int capacity;
    
    private int hash(K key) {
        // Handle null keys
        if (key == null) return 0;
        return Math.abs(key.hashCode()) % capacity;
    }
    
    @SuppressWarnings("unchecked")
    public HashMapChaining(int cap) {
        capacity = cap;
        size = 0;
        buckets = (Node<K, V>[]) new Node[capacity];
    }
    
    public void insert(K key, V value) {
        int idx = hash(key);
        Node<K, V> curr = buckets[idx];
        while (curr != null) {
            if (curr.key.equals(key)) { 
                curr.value = value; 
                return; 
            }
            curr = curr.next;
        }
        Node<K, V> newNode = new Node<>(key, value);
        newNode.next = buckets[idx];
        buckets[idx] = newNode;
        size++;
    }
    
    public boolean find(K key, V[] out) {
        int idx = hash(key);
        Node<K, V> curr = buckets[idx];
        while (curr != null) {
            if (curr.key.equals(key)) { 
                out[0] = curr.value; 
                return true; 
            }
            curr = curr.next;
        }
        return false;
    }
    // delete, destructor omitted for brevity
}
```

**When to use**: Most general purpose; handles high load factor well.

### 2.2 Open Addressing

**What**: All entries are stored in the array itself. When a collision occurs, the table is probed to find an empty slot.

**Probing sequences**:

- **Linear probing**: `index = (hash + i) % m` for i = 0,1,2,...
  - Advantages: Cache friendly.
  - Disadvantage: Primary clustering → long runs of occupied slots.

- **Quadratic probing**: `index = (hash + c1*i + c2*i²) % m`.
  - Reduces clustering but may not probe all slots.

- **Double hashing**: `index = (hash1 + i * hash2(key)) % m`, where `hash2` is a second hash function.
  - Provides good distribution, avoids clustering.

**Performance**: Sensitive to load factor; typically keep α < 0.7.

```java
class HashMapOpenAddressing {
    private static class Entry {
        int key;
        int value;
        
        Entry(int key, int value) {
            this.key = key;
            this.value = value;
        }
    }
    
    private Entry[] table;
    private boolean[] occupied;
    private boolean[] deleted; // deleted flag for lazy deletion
    private int capacity;
    private int size;
    
    private int hash1(int key) { return key % capacity; }
    private int hash2(int key) { return 1 + (key % (capacity - 1)); }
    
    public HashMapOpenAddressing(int cap) {
        capacity = cap;
        size = 0;
        table = new Entry[capacity];
        occupied = new boolean[capacity];
        deleted = new boolean[capacity];
    }
    
    public void insert(int key, int value) {
        int idx = hash1(key);
        int step = hash2(key);
        for (int i = 0; i < capacity; ++i) {
            int probe = (idx + i * step) % capacity;
            if (!occupied[probe] || deleted[probe]) {
                table[probe] = new Entry(key, value);
                occupied[probe] = true;
                deleted[probe] = false;
                size++;
                return;
            }
            if (occupied[probe] && table[probe].key == key) {
                table[probe].value = value; // update
                return;
            }
        }
        // table full – rehash needed
    }
    // find and erase similar
};
```

## 3. Load Factor and Rehashing

**Load factor** α = number of entries / table size.

- For chaining, α > 1 is acceptable (average chain length = α).
- For open addressing, keep α < 0.7 to avoid excessive probing.

**Rehashing**: When α exceeds a threshold (e.g., 0.75), allocate a larger table (usually double size) and re‑insert all entries using the new hash function.

```java
void rehash() {
    int newCapacity = capacity * 2;
    Entry[] oldTable = table;
    boolean[] oldOccupied = occupied;
    capacity = newCapacity;
    table = new Entry[capacity];
    occupied = new boolean[capacity];
    deleted = new boolean[capacity];
    size = 0;
    for (int i = 0; i < oldTable.length; ++i) {
        if (oldOccupied[i] && !deleted[i])
            insert(oldTable[i].key, oldTable[i].value);
    }
}
```

## 4. Hash Map and Hash Set Implementations

### 4.1 Hash Map (Dictionary)

Stores key‑value pairs. C++ `std::unordered_map` (average O(1) operations).

### 4.2 Hash Set

Stores only keys (no values). C++ `std::unordered_set`.

**Simple hash set using chaining**:

```java
class HashSet {
    private List<List<Integer>> buckets;
    
    private int hash(int key) { return Math.abs(key) % buckets.size(); }
    
    public HashSet(int cap) {
        buckets = new ArrayList<>(cap);
        for (int i = 0; i < cap; i++) {
            buckets.add(new ArrayList<>());
        }
    }
    
    public void add(int key) {
        int idx = hash(key);
        List<Integer> bucket = buckets.get(idx);
        if (bucket.contains(key)) return;
        bucket.add(key);
    }
    
    public boolean contains(int key) {
        int idx = hash(key);
        List<Integer> bucket = buckets.get(idx);
        return bucket.contains(key);
    }
    
    public void remove(int key) {
        int idx = hash(key);
        List<Integer> bucket = buckets.get(idx);
        bucket.remove(Integer.valueOf(key));
    }
};
```

## 5. Applications

### 5.1 Two‑Sum Problem

**Problem**: Given an array of integers and a target, return indices of two numbers that add to target.

**Approach**: Use a hash map from value to index. For each element `nums[i]`, check if `target - nums[i]` exists in the map.

```java
int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> m = new HashMap<>(); // value -> index
    for (int i = 0; i < nums.length; ++i) {
        int complement = target - nums[i];
        if (m.containsKey(complement))
            return new int[] {m.get(complement), i};
        m.put(nums[i], i);
    }
    return new int[] {};
}
```

**Time**: O(n). **Space**: O(n).

### 5.2 Subarray Sum Equals K

**Problem**: Count number of contiguous subarrays whose sum equals k.

**Approach**: Use prefix sum and a hash map storing frequency of each prefix sum. For each prefix sum `curr`, add the count of `curr - k` seen so far.

```java
int subarraySum(int[] nums, int k) {
    Map<Integer, Integer> freq = new HashMap<>();
    freq.put(0, 1); // empty prefix sum
    int prefix = 0, count = 0;
    for (int x : nums) {
        prefix += x;
        count += freq.getOrDefault(prefix - k, 0);
        freq.put(prefix, freq.getOrDefault(prefix, 0) + 1);
    }
    return count;
}
```

**Time**: O(n). **Space**: O(n).

### 5.3 Longest Consecutive Sequence

**Problem**: Find the length of the longest consecutive elements sequence in unsorted array (O(n) time).

**Approach**: Insert all numbers into a hash set. For each number, if its predecessor (`num-1`) is not in the set, it is the start of a sequence. Then count consecutive numbers.

```java
int longestConsecutive(int[] nums) {
    Set<Integer> s = new HashSet<>();
    for (int num : nums) {
        s.add(num);
    }
    int best = 0;
    for (int x : nums) {
        if (!s.contains(x - 1)) {
            int len = 1;
            while (s.contains(x + len)) len++;
            best = Math.max(best, len);
        }
    }
    return best;
}
```

**Time**: O(n) (each element visited at most twice). **Space**: O(n).

### 5.4 Group Anagrams

**Problem**: Group strings that are anagrams of each other.

**Approach**: For each string, sort its characters to form a key, or use a frequency count as key.

```java
List<List<String>> groupAnagrams(String[] strs) {
    Map<String, List<String>> groups = new HashMap<>();
    for (String s : strs) {
        char[] chars = s.toCharArray();
        Arrays.sort(chars);
        String key = new String(chars);
        groups.computeIfAbsent(key, k -> new ArrayList<>()).add(s);
    }
    return new ArrayList<>(groups.values());
}
```

**Time**: O(n * k log k) where k is max string length. **Space**: O(nk).

### 5.5 LRU Cache (Hash Map + Doubly Linked List)

**Problem**: Design a cache that evicts the least recently used item when capacity is exceeded.

**Approach**: 
- Hash map: key → node pointer (for O(1) access).
- Doubly linked list: nodes in order of recent use (most recent at head, least at tail).

**Operations**:
- `get(key)`: if key exists, move node to head, return value.
- `put(key, value)`: if key exists, update value and move to head; else insert new node at head; if over capacity, remove tail.

```java
class LRUCache {
    struct Node {
        int key, val;
        Node *prev, *next;
        Node(int k, int v) : key(k), val(v), prev(nullptr), next(nullptr) {}
    };
    unordered_map<int, Node*> m;
    Node *head, *tail;
    int cap, size;

    void addToHead(Node* node) {
        node->next = head->next;
        node->prev = head;
        head->next->prev = node;
        head->next = node;
    }
    void removeNode(Node* node) {
        node->prev->next = node->next;
        node->next->prev = node->prev;
    }
    void moveToHead(Node* node) {
        removeNode(node);
        addToHead(node);
    }
    Node* removeTail() {
        Node* node = tail->prev;
        removeNode(node);
        return node;
    }
public:
    LRUCache(int capacity) : cap(capacity), size(0) {
        head = new Node(-1, -1);
        tail = new Node(-1, -1);
        head->next = tail;
        tail->prev = head;
    }
    int get(int key) {
        if (m.find(key) == m.end()) return -1;
        Node* node = m[key];
        moveToHead(node);
        return node->val;
    }
    void put(int key, int value) {
        if (m.find(key) != m.end()) {
            Node* node = m[key];
            node->val = value;
            moveToHead(node);
            return;
        }
        Node* newNode = new Node(key, value);
        m[key] = newNode;
        addToHead(newNode);
        size++;
        if (size > cap) {
            Node* toRemove = removeTail();
            m.erase(toRemove->key);
            delete toRemove;
            size--;
        }
    }
};
```

**Time**: O(1) per operation. **Space**: O(capacity).

**Real-life analogy**: A librarian keeps frequently borrowed books on a shelf near the entrance (most recent). When new books arrive, the least recently borrowed book is moved to storage.

## 6. Summary

| Concept | Key Points |
|---------|-------------|
| Hash function | Maps key to index; uniform distribution reduces collisions |
| Chaining | Simple, handles α > 1; uses linked lists per bucket |
| Open addressing | Stores all entries in array; uses probing sequences |
| Load factor | n/m; rehash when exceeding threshold (e.g., 0.75) |
| Hash map / set | Average O(1) operations; `unordered_map` / `unordered_set` in C++ |
| Two‑sum | Hash map stores seen values |
| Subarray sum = K | Prefix sum + frequency map |
| Longest consecutive | Hash set enables O(n) sequence detection |
| Group anagrams | Sorted string or frequency count as key |
| LRU Cache | Hash map + doubly linked list gives O(1) get/put |

The next chapter will cover binary trees, binary search trees (BST), AVL trees, and tree traversals.
