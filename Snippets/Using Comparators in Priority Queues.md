# Using Comparators in Priority Queues

#### PriorityQueue Functions
* add()
* peek()
* poll()
* remove()
* contains()

#### Implementation
##### Basic class
```java

  static class Node  {
	String name;
	int priority;
	Node(String n,int p){
		name = n;
		priority = p;
	}
  }
```
##### Declaring new class inheriting Comparator
```java
  static class NameCompare implements Comparator<Node>{
    @Override
    public int compare(Node a,Node b) { 
      return (a.name).compareTo(b.name); 
    }
  }
```
##### Routine print function
```java
  static void print(PriorityQueue<Node> pq,String str){
    System.out.println(str);
    for(Node n:pq) System.out.println(n.name);
  }
 ```


#### Ways of providing Comparators

```java
  public static void main (String[] args) throws java.lang.Exception	{
	Node a = new Node("Senior",2020);
	Node b = new Node("Junior",2022);
		
	PriorityQueue<Node> pq_name = new PriorityQueue<>(new NameCompare());
	pq_name.add(a);
	pq_name.add(b);
	print(pq_name,"Comparing name:");
	
	PriorityQueue<Node> pq_priority = new PriorityQueue<Node>((x,y)->Integer.compare(x.year,y.year));
	//for reversing, multiply with -1
	pq_priority.add(a);
	pq_priority.add(b);
	print(pq_priority,"Comparing seniority:");
	
	PriorityQueue<Node> pq_name_rev = new PriorityQueue<Node>(new NameCompare().reversed());
	pq_name_rev.add(a);
	pq_name_rev.add(b);
	print(pq_name_rev,"Comparing name reversed:");
}
```
##### Output:
```
Comparing name:
Junior
Senior
Comparing seniority:
Senior
Junior
Comparing name reversed:
Senior
Junior
```
