# Efficiency
- Time
- Space

# Space Eficiency

Usually proportional to size to be stored.
As the number of element you are storing changes, size to be stored is changes.
Space efficiency is usually not so much of a concern.

# Time Efficiency
- How long does it take ?
- Storage time- single item
- Retrieval time - single item
- Retrieval time - search

How do you measure time efficiency ?  

Bigger collection = longer times  

A factor of N.  

## O(N) --> Big O Notation  

How good/bad is the dependence on N?  

**Big O notation**  
- Rough imprecise measurement / classification  
- How much the time depends on collection size ?  
- Broad buckets  

## Linear Time

**Scenario 1**  
Find a token in the jar  

**Strategy**  
Look at tokens one by one  

Time directly proportional to size of the jar  

O(N) --> Depends on the size of collection  
This is the linear time.  
Bigger the jar, longer the finding the token.  

**What if you find it sooner?**  

The thing about Big O is that it does not consider the best case scenario.  
Never depend on luck!  

Big O Notation  
- Worst case estimate  
- Rough / broad estimate  


## Constant Time  

**Scenario 2**  
Pick ANY token from the jar.  

**Strategy**  
Pick the first token you can grab  

**Time is independent of the size of the jar**  

**O(1)**  
Constant time. There is no N because time is independent.  

** It does not mean it's faster, it is just independent of N**  

## Logaritmic Time  

**Scenario 3**  
Find a token in a sorted token stack  

**Strategy**  
Binary Search  

1. Look at the middle  
2. If greater, take first half  
3. If lesser, take second half  
4. Repeat  

Bigger the N, the more the efficiency of algorithm.  
Time does not linearly increase with size of N.  

**O(log N)**  
Logarithmic time  


## Quadratic Time  

**Scenario 4**  
Get duplicate tokens from the jar  

**Strategy**  
1. Take one, compare with every other token.  
2. Repeat  

Bigger the jar, the worse it gets!  

O(N*N)
Quadratic Time  

## How O-Notation Matters  
1. Inherent performance characteristics  
2. Implementation-based characteristics  

**Inherent performance characteristics**  
Searching a list --> O(N)


# ITERATORS  

**How Iterators Work**  
Every collection type has an iterator object on it's own. So, user only interacts
with the iterator object of the collection that is been used. User do not have to
know the implementation of iterating through the collection.Just talk to the
iterator guy!  

**Using Iterators**  

You can get iterator object from any collection type.  
Here is how the iterator works :  
The Iterator Interface  
```
    public Iterator <E> {
	boolean hasNext(); // Are there more elements ? 
	E next(); 	   // Get the next element in this iteration  
	void remove();     // Remove the last element returned by the iterator  
	default void forEachRemaining(Consumer <? super E> action);
    }
```  

**Printing all elements in an ArrayList**  

```
ArrayList<String> names = new ArrayList<>();

for(int i=0;i<20;i++){
    names.add("name "+i);
}

for(int i = 0 ; i<20; i++) {
    System.out.println(names.get(i));
}
```
If you change arraylist to any other collection types like hashmap or sets, the code
above will not work.This is where the Iterator pattern comes in : 

```
ArrayList<String> names = new ArrayList<>();

for(int i = 0 ;i<20;i++){
    names.add("name "+i);
}

Iterator <String> iterator = names.iterator(); // We created an iterator for that arraylist  

while(iterator.hasNext()){
    System.out.println(iterator.next()) // While iterator has a next element, we printed all the next elementds one by one  
}
```  

**You can create multiple iterators of the same collection type.Each iterator
will have it's own pointer.For example, you created iterator1 for this arraylist
and called iterator1.next() 3 times, iterator1 will be pointing the 3rd element.
And if you created iterator2 for the same arraylist and called iterator2.next()
you will get the first element in the arraylist.**  

Iterators sometimes don't like modifications in the collection.You can do that
in collections that support this.

**Do not modify the collection when using Iterators!!**  

**For-each loop is basically a syntax for iterators**
** It's basically calling an iterator **  

```
for (Type element : Iterable){

}
```
What is iterable ?  

If you have an object which is iterable,  
A) You can get an iterator out of it  
B) You can literally use that in a for-each loop.  

Iterators are far more advanced from for-each loop.  
You can decide when to call .next, how many iterations you want, basically  
you control everything in iterators.  

All point of for-each loop is basically the simplicity of syntax and easy writing.










