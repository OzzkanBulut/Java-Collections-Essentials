## Sets  

**A collection with no duplicate elements**  

**Common use case**  
Classification of items  

**Sets Example**  

Assign students to lectures  

- Students A,B and C
- Lectures 1 and 2  

**Steps**  

1. Assign Student A to Lecture 1  
2. Assign Student B to Lecture 2  
3. Assign Student C to Lecture 1  
4. Assign Student A to Lecture 1  

**What should happen on Step 4**  

**What happens if we use ArrayList**  

**Steps with ArrayList**  

1. If not already assigned, assign Student A to Lecture 1  
2. If not already assigned, assign Student B to Lecture 2  
3. If not already assigned, assign Student C to Lecture 1  
4. If not already assigned, assign Student A to Lecture 1  

**Checking for Duplicates**  
Wouldn't it be nice if we could use a data structure to avoid this?  

**Sets**  
No duplicate elements are allowed:  
**Contain no pair of elements e1 and e2 such that e1.equals(e)**  
**If you use default equals set will allow duplicates because they are different instances even
though they have the same properties.Because of that, you we need to override the equals method in the insance**  

**What about null?**  

Set can contain utmost one null element.  
The second null element breaks the equality contract.  

## Sets - Code  

```
public class SetMain {
  
    public static void main(String[]args){

        Set<String> names = new HashSet<>();
        names.add("Name A");
        names.add("Name B");
        System.out.println(names);
	// In the list, there is a concept of order
        // But in sets, there is no insertion order 
        names.add("Name A");
        System.out.println(names);

        names.remove("Name A");
        System.out.println(names);
    }
}
```

## HashSet 

**The Alphabetical file drawer**  
Implemented by a hash table  

**HashSet Structure**  

![image](https://user-images.githubusercontent.com/67637654/201107395-70d35043-c684-4bfc-a23b-71cde253062c.png)

**HashSet Bucket structure**  
- Contiguous  
- LinkedList  
**Java implementation of hashset uses the linkedlist**  

**HashSet Efficiency**  

- add -> O(1) 
- remove -> O(1)  (You only look at the hashcode to find the element, hashset size does not matter)
- contains -> O(1) (It's independent of N, you just look hash collisions)

**Initial capacity**  
Default, hashset creates 16 buckets  

**Hash Load Factor**  
number of elements / number of buckets  

Every time you add an element to the hash set , hashset calculates the load factor.  
You add one element, load factor will be 1/16. 

**Rehashing**  
When hash load is too high  
Double the capacity  

Anytime the load factor reaches 0.75, it rehashes and doubles the capacity.  

**Load Factor**  
is 0.75  
- Initial number of buckets: 16  
- Number of elements : 12  
- 12/16: 0.75  
- Rehash Time !

**When object1.equals(object2) is true, object1.hashCode() == object2.hashCode()**  

## LinkedHashSet  
![image](https://user-images.githubusercontent.com/67637654/201107010-20184549-72c5-4f65-81c9-aac060064550.png)  

Every added element holds a pointer to the next element  
Like a linkedlist  

**Advantages**  
- Insertion order  
- Ordered iteration O(1) time  

**LinkedHashSet Performance**  
- add --> O(1)
- contains --> O(1) 
- next --> O(1)  

Nothing too different from hashset.Only there are pointers and ordered iteration  

## TreeSet  
![image](https://user-images.githubusercontent.com/67637654/201107192-16620d73-d90a-439f-89b9-1a68d4b1ac85.png)

**TreeSet Walkthrough**  
```
--> 200, 150, 275, 3, 175, 300  

          200
   150           275
3       175            300 
This is the Binary Search Tree(BST)
This makes searching for an element much more faster!
```

**TreeSet Requirements**  
Must be Comparable(If you want to create a treeset of students, student class must be implement comparable interface)

compareTo and equals  
Must be consistent!  

**TreeSet Performance**  
- add --> O(log n)
- contains --> O(log n)  
- iteration --> O(log n)
Everything is O(log n) because you are doing a binary search  

**Imbalanced trees**  
1
  2
    3
      4
        5
This is essentially a linked list.
Balancing a tree with balance operation costs O(log n) time.


## Sets - when to use what  

**When to use Set**  

- Position is not important  
- Fast lookup  
- Fast contains check  
- No Duplicates!  

**HashSet vs TreeSet**  

**Use HashSet when**  
- Order is not important  
- Sorting is not important  
- Good hashing strategy  
- Predictable load factor  (if you know the element amount)  
- 






 

  
