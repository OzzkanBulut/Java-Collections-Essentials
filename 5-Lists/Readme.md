## Lists  
An ordered collection of elements.  

**Common usecase**  
Storing items in order with index based access  

**Lists Example**  
List of students in a school  

Students with IDs  

1. Add(enroll) new students  
2. Process all students in order  
  - By ID for sending notifications
  - By name for attendance  
  - By grade for scholarships  
3. Access a student's record given ID  

**Steps**
Ordered enrolling of students  

1. Enroll Student A with ID 1
2. Enroll Student B with ID 2
3. Enroll Student C with ID 3  

**Add Operations**  
```
boolean add(E e);
boolean addAll(Collection <? extends E> c);

void add(int index, E element);
boolean addAll(int index, Collection<? extends E> c);
```

**Remove Operations**  
```
boolean remove(Object o);
boolean removeAll(Collection<?> c);

E remove(int index);

boolean retainAll(Collection<?>c);
void clear();
```

**Replace Operations**  
```
E set(int index, E element);
default void replaceAll(UnaryOperator<E> operator) // Replace with result of operator
```

**Inspect Operations**  
```
boolean contains(Object o);
boolean containsAll(Collection<?>c);

int indexOf(Object o);
int lastIndexOf(Object o);

boolean isEmpty();

int size();
```

**Retrieve Operations**  
```
E get(int index);

List<E> subList(int fromIndex, int toIndex)
// Returns a view of the portion of this list between the specific index locations
// fromIndex , inclusive; and toIndex, exclusive
```

**Processing Operations**  
```
Iterator<E> iterator();
ListIterator<E> listIterator();
ListIterator<E> listIterator(int index); // Starting at index
default Spliterator<E> spliterator();
ListIterator<E> listIterator();
```

**Lists - Code**  

```
public class ArrayListMain{
    
    public static void main(String[] args){
        List<String> names = new ArrayList<>(); --> This is a list implementation
        names.add("name A");
        names.add("name B");
        System.out.println(names);
        
        names.add("name A"); // Allows duplicate
        
        names.set(2,"Name C"); // replace name A with name C
        
        System.out.println(names.get(0)); // Get the first element

	System.out.println(names.get(200)); // index out of bounds exception  

        names.add(0,"name D");//Insert name D to first position, It's different from set! we inserted a new element

        names.remove(1); // remove the element at index 1

        names.remove("name C"); // Finds the element and removes it  
    }
}
```
## ArrayList  

**You don't have to specify the size**  
When you add at a certain position, array shifts after that index.  
This is a index-positioned collection.  
When you remove an element at a certain positions, array shifts left after that index.  

**ArrayList Performance**  

- get --> O(1) // Get an element from arraylist is not dependent of N, No matter how big or small the arraylist, it only takes 1
- set --> O(1) // This takes same time with get  
- contains --> O(N) --> Because it has to look every element in the arraylist to see if it exists  
- remove(0) --> O(N) // Actually, removing an element at index 0 takes O(1), **But, after removing you have to shift every element to the left, and because of this it takes O(n) time**  
- add(0) --> O(N) // Same with remove

**ArrayList** 
Finite amount of space  

What if it overflows ?  

When you try to add an element to the full arraylist, arraylist resizes.  

**ArrayList doubles space when it runs out, and copies the elements to the new arraylist**  

**ArrayList - add Performance**  

- Best case -> O(1)  
- Worst case -> O(N) // In case of arraylist is full and we have to resize it and copy all the elements to the new ArrayList  
- Most cases -> O(1)  

**In Bıg O notation, you have to consider the worst case, but here, this is not very helpful**  
**It's not fair to assume add performance is O(N), because it's very rare. Because of that, it's assumed O(1)**  


**ArrayList - add Performance**
O(1)  
Amortized time  

## Linked List  

**LinkedList - Structure**  
(ss 0.30)  
Think of it like a students holding hands  

**LinkedList - Performance**  

- get() --> O(N)  
- set() --> O(N)
- contains() --> O(N)

**LinkedList - performance(add and remove)**  

- remove(0) --> O(1)  
- add(0) --> O(1)  
- add --> ?  
- remove --> ? 

**Seperate the get from the add/remove**  
- get - O(N)  
- add - O(1)  
- remove - O(1)  
In general, adding something does O(N), but actually, what takes O(N) is getting
to the position, after reaching the position, adding and removing only takes O(1).

Difference between arraylist and linkedlist is, when you add/remove element in the
arraylist, you need to shift other elements, which is why it takesO(N).

But in linkedlist, there is no need to shift.What takes O(N) is that in linkedlist
you can not reach the element at a certain position immediately.Reaching the element
takes O(N) time.   

## List - When to use what ? 

**When to Use List**  
- Position important  
- Duplicates don't matter 
- Iteration use cases - do x for all elements  

**ArrayList vs LinkedList**  
- Position based access --> ArrayList  
- Constant and random insertions and removals --> LinkedList  **There is no overflow in likedlist**
- Iteration --> either  


