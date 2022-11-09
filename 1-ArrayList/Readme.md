## ArrayList  

**"Replacement" for arrays**  

**Structure**  
Collections --> List --> ArrayList  

Collections is a top level interface.   
List is also an interface.  
And ArrayList is the implementation of List interface.  

**Using ArrayList**  

ArrayList<String> names = new ArrayList<>();  
**We are not specifying the size here!**  
Do not worry about the size.

```
for(int i = 0; i<20; i++) { 
  names.add("name"+i);
}

for(int i = 0; i<20; i++) {
   System.out.println(names.get(i));
}
```
**Difference from Array**  
- You don't have to specify the size
- No special syntax 
- Anything we do on the arraylist, it is a method on the object instance itself  

names.indexOf("name 4") --> Is gonna give us 5
  
  
  
  
  
  
  
