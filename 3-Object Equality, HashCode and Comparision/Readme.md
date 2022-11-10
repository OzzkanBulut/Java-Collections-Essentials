## Equality in Object Oriented Programming  

**Equality**  
The == operator  

5 == 5  

false == false  

**Equality with Objects**  

References pointing to the same objects are equal.  
References pointing to the different objects are not equal.  

**What if you have 2 objects that contain same data? Are they equal ?**  

Java will say they are not equal.Because they are stored in the different locations of memory.

Only you know what equivalence means  

**The equals() method**  

```
public class Student {
    private String firstName;
    private String lastName;
    private int id;
    private String department;

    public Student(String firstName, String lastName, int id, String department){ 
        
        this.firstName = firstName;
        this.lastName = lastName;
        this.id = id;
        this.department = department;
    }
........

    Student student1 = new Student(Özkan,Bulut,1,Pc);
    Student student2 = new Student(Özkan,Bulut,1,Pc);

    System.out.println(student1 == student2); // It will print false
    System.out.println(student1.equals(student2)); // It will also print false , but if you override equals method in the student class, it will print true
    // The reason .equals prints false is because in default, it is same with == operator
```  

## Hashing and Hash Codes  

**The hashing concept**  
Hashing is the process of taking an object and reducing it into a one value.  

We do that by applying a hashing function.  

![image](https://user-images.githubusercontent.com/67637654/201105383-2f375080-1aeb-43a7-a2c4-2f540271f8f3.png)

Let's say we have a student files drawers.When we assign each drawer to a letter
and put students who have the same first letter with that letter, this is basically
a hashing function.  

![image](https://user-images.githubusercontent.com/67637654/201105426-339c3a1c-2c5a-4b10-a30e-00fd673dd2dc.png)
This is a one to many mapping.  

What maps to that student name letter, we only go to that drawer.  

This is hashing in general.  

**hashCode in Java**  


**hashCode is a method on Object**  

public int hashCode();  

Every object in java has a hashCode in it.  

**Running default hashCode implementation**  

```
public static void main(String[]args){
    
    Student student1 = new Studfent("Foo","Bar",1,"Science");
    Student student2 = new Studfent("Foo","Bar",1,"Science");

    System.out.println(student1.hashCode());
    System.out.println(student2.hashCode());
}
    Output:
    2001049719
    1528902577
```
If you use default hashCode, you get two differnet weird numbers.  
Just like with equals, point of a hashCode is for you to implement what it needs
to return.  

**Eamining IDE implementation**  

If two objects are considered equal by the equals method, then their hashCode
should return the same value.Because they are considered equal and they have to be
in the same group.  

## Object Ordering  

** What is needed for ordering ?**  

**Comparision  **   

5 > 4  

** Sorting**  

[5, 3, 4 ] -> [3, 4, 5]  


** Sorting with Objects **  

[obj1, obj2, obj3] -> ?  

**What does this mean?**  

objA > objB  

1. There's object state in objA and objB  (There is some data on objA)
2. There is a clear definiton of comparision of those values  
3. Individual values or combination of values  

**Not all objects are comparable!**  

Example: Two database connection instances  

You can not compare them  

## The Comparable Interface  

**Indicates that an object is comparable**  

```
public interface Comparable<T> {
    public int compareTo(T o);
}
```  
**Why is the return type an int ?**  

Because there are three possible return values:  

1. Argument object is greater than this object  
2. Argument object is lesser than this object  
3. They are both the same  
When we say same, we do not mean equal. They are the same in terms of what we are comparing.  

For the criteria that we are using for comparing, they are essentially the same.  

Is this student is greater than other student in terms of grades?  
Yes, they are the same.Only in grades.That does not mean these students are equal.  

**Three Possible Return Values**  

1.**Negative value** Argument object is greater than this object  
2.**Positive value** Argument object is lesser than this object  
3.**Zero** They are both the same  

**Implementing the Comparable Interface**  

```
public class Student implements Comparable<Student> {
    
    @Override
    public int compareTo(Student o){
    
        return this.id - o.getId();
    //If this.id is greater value will be positive, if they are equal value will be 0  
    and if o.id is greater, the value will be negative.
    This is a shortcut.      
}
```  

**Sorting Comparable Implementations**  

```
Student studen1 = new Student("Foo","Bar",2,"Science");
Student studen2 = new Student("Bar","Bar",1,"Commerce");
Student studen3 = new Student("Blah","Bar",3,"Arts");  

ArrayList<Student> students = new ArrayList<>();
students.add(student2);
students.add(student1);
students.add(student3);

students.sort(null); // This is gonna sort for id's
This is a natural sorting.  

**Custom Comparators**  

Sometimes order depends on context. Not on id.  

**Sorting students**  
- By grade for ranking  
- By height for physical training exercises  
- By name for attendance  

**But there is only one compareTo method!**  

Solution --> Custom Comparators  

**The Comparator Interface**  

```
```
public interface Comparator<T> {
    int compare(T o1, T o2);
}
```
"Third party" comparator  
Takes two objects of a type.  

**Multiple Comparators**  
You can have as many comparators as you want.  
  
```
public class StudentLastNameComparator implements Comparator<Student>{
    int compare(Student o1, student o2){
    }
}
```
  
```
public class StudentHeightComparator implements Comparator<Student>{
    int compare(Student o1, student o2){
    }
}
```
  
```
public class StudentGradeComparator implements Comparator<Student>{
    int compare(Student o1, student o2){
    }
}
```  

**Sort method**  

students.sort(new StudentGradeComparator()); --> Sort the students list based on the grade  
