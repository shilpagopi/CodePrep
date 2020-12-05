# Overriding Hashcode and Equals for User defined classes
```java
class Emp implements Comparable<Emp>{
    @Override
    public boolean equals(Object obj){
        if(obj==null)
            return false;
        if (this==obj)
            return true;
        if(this.getClass()!=obj.getClass())
            return false;
        Emp emp = (Emp) obj;
        return this.id==emp.id && company.equals(emp.company);
    }

    @Override
    public int hashCode(){
        int prime = 31;
        int result = company == null ? 1 : company.hashCode();
        result = prime * result + Integer.hashCode(id);
        return result;
    }
    
    @Override
    public int compareTo(Emp e){
        int i = Integer.compare(id,e.id);
        if (i!=0)
            return i;
        return company.compareTo(e.company);
    }
 }
```
