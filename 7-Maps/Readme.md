## Map
Like a dictionary  
**Does not extend from the collection interface.**
**And because it does not extend from the collection interface, does not have
iterable interface**  

```
public class MapMain {

    public static void main(String[] args) {

        Map<Integer,Student> students = new HashMap<>();
        Student student1 = new Student("Foo","Bar",2,"Science");
        Student student2 = new Student("Bar","Baz",1,"Commerce");
        Student student3 = new Student("Blah","Bar",3,"Arts");
        
        students.put(student1.getId(), student1);
        students.put(student2.getId(), student2);  
        students.put(student3.getId(), student3);

        System.out.println(students);

        System.out.println(students.get(1)); // Gets the key number 1
        
        students.put(200,null);

        System.out.println(students.get(200)); // Prints null --> This is a bad practice, dont do this!
        System.out.println(students.get(300)); // Also prints null
	
	for(Integer key : students.keySet()){ // Get all the keys(id's in the map)
            System.out.println(key);
        }

        for(Student value : students.values()){
        
           System.out.println(value);  // Get all the values(students in the map)

        }        

	for(Map.Entry<Integer,Student> entry : students.entrySet()) { // Get keys and values at the same time
            // Entry is like a one row of the map, gives us both key and the value at the same time
            System.out.println(entry.getKey()+ "-->" + entry.getValue());
        }

        System.out.println(
	           students.getOrDefault(100, new Student("Foo","asdas",2,"sdfsd"));
	) // If there is a key 100, give me that. If not, create this instance and return me that
        
        // If there is not a key 1, create this instance and assign it to the key 1
        students.putIfAbsent(1, new Student("Foo","asdas",2,"sdfsd"));

```

**HashMap Performance**
- get --> O(1) 
- containsKey --> O(1)
- put --> O(1)

  













