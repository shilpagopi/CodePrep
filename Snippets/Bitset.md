```java
BitSet bitset = new BitSet(10);
bitset.set(3);
bitset.flip(2);
bitset.set(1,true);
bitset.flip(6,8); //excluding 8th index
System.out.println(bitset);

System.out.println(bitset.cardinality()); // count of set bits
System.out.println(bitset.nextSetBit(4)); // Returns index of first set bit that occurs on or after the specified index.
// nextClearBit(), previousSetBit()
bitset.xor(new BitSet(10)); // and, andNot, or
System.out.println(bitset.equals(new BitSet(10)));
```
