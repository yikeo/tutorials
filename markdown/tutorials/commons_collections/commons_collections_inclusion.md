# Apache Commons Collections - Inclusion
CollectionUtils class of Apache Commons Collections library provides various utility methods for common operations covering wide range of use cases. It helps avoid writing boilerplate code. This library is very useful prior to jdk 8 as similar functionalities are now provided in Java 8's Stream API.

## Checking sublist
isSubCollection() method of CollectionUtils can be used to check if a collection contains the given collection or not.

## Declaration
Following is the declaration for

**org.apache.commons.collections4.CollectionUtils.isSubCollection()** method −

```
public static boolean isSubCollection(Collection<?> a,
   Collection<?> b)
```
## Parameters
   * **a** − The first (sub) collection, must not be null.
   * **b** − The second (super) collection, must not be null.

## Return Value
True if and only if a is a sub-collection of b.

## Example
The following example shows the usage of org.apache.commons.collections4.CollectionUtils.isSubCollection() method. We'll check a list is part of another list or not.

```
import java.util.Arrays;
import java.util.List;

import org.apache.commons.collections4.CollectionUtils;

public class CollectionUtilsTester {
   public static void main(String[] args) {
      //checking inclusion
      List<String> list1 = Arrays.asList("A","A","A","C","B","B");
      List<String> list2 = Arrays.asList("A","A","B","B");

      System.out.println("List 1: " + list1);
      System.out.println("List 2: " + list2);
      System.out.println("Is List 2 contained in List 1: " 
         + CollectionUtils.isSubCollection(list2, list1));
   }
}
```
## Output
It will print the following result.

```
List 1: [A, A, A, C, B, B]
List 2: [A, A, B, B]
Is List 2 contained in List 1: true
```

[Previous Page](../commons_collections/commons_collections_safe_checks.md) [Next Page](../commons_collections/commons_collections_intersection.md) 
