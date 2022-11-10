## The Collection Interface  

**Not to be confused with Collections**  
The methods in collections are support all of the collections api's.  

The collection is the interface which is the parent of all collections.  

**Lowest common denominator**  
To support all collections  

Collection is the sub interface of Iterable.  
Any collection can be iterated over.  
	
**Map is not a sub interace of Collection!**  

** The Collection Interface**  

**Method types**  

-**Add** add, addall--> Take a collection and add all it's elements to another collection
-**Remove** remove, removeAll, clear, retainAll,
-**Inspect** isEmpty, size  
-**Process** iterator, stream, toArray  

**Things To Remember**  
- Root interaface in the collection hierarchy  
- No direct implementation in the JDK  
- Sub interfaces for collection types --> like set, List  
- Generic methods for adding and removing elements from the collection  
- Underlying implementation decides what happens when the methods are called  

**Collection just provides the contract, it's up to the implementation what's gonna happen!**
