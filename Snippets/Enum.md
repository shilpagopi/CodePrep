# Enum - A specialized class
* Also called Java enumeration type
* to model a fixed set of constants in Java 
* to declare the fields as final and static.
* to enforce **compile time type safety**. 
* can add abstract and concrete methods 
* comparable,singleton and serializable
* cannot extend any other class because Java does not support multiple inheritance
* if an enum is a member of a class, it’s implicitly static
* for enum constants, equals() and "==" evaluates to same result

### * Logically, each enum is an instance of enum type itself.

```java
public enum Direction 
{
   EAST, WEST, NORTH, SOUTH;
}
```
```java
final class Direction extends Enum<Direction> 
{
    public final static Direction EAST = new Direction();
    public final static Direction WEST = new Direction();
    public final static Direction NORTH = new Direction();
    public final static Direction SOUTH = new Direction();
}
```
### * ordinal() - returns array index based on sequence of declaration

### * values() - returns enum array

### * valueOf() - convert string to enum instance

```java
System.out.println(north);        //Prints NORTH
System.out.println(Direction.EAST.ordinal());     //Prints 0
Direction[] directions = Direction.values(); 
Direction east = Direction.valueOf("EAST");
```
### * Constructors
* By default, enums don’t require constructor definitions and their default values are always the string used in the declaration.
* Enum cannot have a default no-argument constructor and all its constructors are private.

```java
public enum Direction 
{
    // enum fields
    EAST(0), WEST(180), NORTH(90), SOUTH(270);
 
    // constructor
    private Direction(final int angle) {
        this.angle = angle;
    }
 
    // internal state
    private int angle;
 
    public int getAngle() {
        return angle;
    }
    
    protected void printDirection() 
    {
        System.out.println("You are moving in " + this + " direction");
    }
}

//usage : System.out.println(Direction.NORTH.getAngle()); //90
//usage : Direction.NORTH.printDirection(); // "You are moving in north direction"
```

