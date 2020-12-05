# Overriding Hashcode and Equals for User defined classes
```java
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
```
