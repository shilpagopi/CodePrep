``` 'java'
import java.util.*;

class Student implements Comparable<Student> {
    int age;
    String name;

    Student(int a,String n) {  
        this.age=a;
        this.name = n;
    }

    @Override
    public int compareTo(Student s) {
        int comp = Integer.compare(age,s.age); //return older
        return comp!=0? comp: name.compareTo(s.name); //return alphabetical if same age
    }
  }
  
public class Main {
  
  public static void main(String[] args) {
        Student s1 = new Student(1, "C");
        Student s2 = new Student(1, "B");
        Student s3 = new Student(3, "A");
        PriorityQueue<Student> pq = new PriorityQueue<>();
        pq.add(s1);
        pq.add(s2);
        pq.add(s3);
        
        while(pq.size()>0){
            Student s = pq.poll();
            System.out.println(s.age + s.name);
        }
  }
}

Output:
1B
1C
3A
```
