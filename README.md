# Lab-8_202001414

# Name: Rohan Champaneri

# ID: 202001414

## Lab Exercises

```java
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {
@Test
public void testIsHealthy() {
    Boa boa1 = new Boa("Sneaky", 6, "granola bars");
    assertTrue(boa1.isHealthy());
   
    Boa boa2 = new Boa("Slithery", 8, "pizza");
    assertFalse(boa2.isHealthy());
}

@Test
public void testFitsInCage() {
    Boa boa1 = new Boa("Slinky", 4, "mice");
    assertTrue(boa1.fitsInCage(5));
    assertFalse(boa1.fitsInCage(3));
   
    Boa boa2 = new Boa("Curly", 10, "rabbits");
    assertTrue(boa2.fitsInCage(12));
    assertFalse(boa2.fitsInCage(9));
}
}
```
The test cases are aimed at verifying the functionality of the Boa class. In the first test case, the isHealthy method is tested by creating two Boa objects with different favorite foods, and checking if the method returns true for the first object and false for the second.

In the second test case, the fitsInCage method is tested by creating two Boa objects with different lengths and verifying whether they can fit in cages of varying lengths. The first Boa is expected to fit in a cage of length 5 but not 3, while the second Boa is expected to fit in a cage of length 12 but not 9.

```java
import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {

private Boa jen;
private Boa ken;

@Before
public void setUp() throws Exception {
    jen = new Boa("Jennifer", 2, "grapes");
    ken = new Boa("Kenneth", 3, "granola bars");
}

@Test
public void testIsHealthy() {
    assertTrue(jen.isHealthy());
    assertTrue(ken.isHealthy());
}

@Test
public void testFitsInCage() {
    assertTrue(jen.fitsInCage(3));
    assertFalse(ken.fitsInCage(2));
}
}
```
In the BoaTest class, private fields were added for jen and ken, which were then initialized in the setUp method. The testIsHealthy and testFitsInCage methods were also modified to use these Boa objects for testing.

It is important to note that the setUp method will be executed before each test method, which means that any modifications made to the Boa objects during a test will not impact the objects used in other tests. This ensures that each test is performed using fresh instances of the objects and any changes made during one test do not interfere with the subsequent tests.

```java
import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {

private Boa jen;
private Boa ken;

@Before
public void setUp() throws Exception {
    jen = new Boa("Jennifer", 2, "grapes");
    ken = new Boa("Kenneth", 3, "granola bars");
}

@Test
public void testIsHealthy() {
    assertTrue(jen.isHealthy());
    assertTrue(ken.isHealthy());
}

@Test
public void testFitsInCage() {
    assertTrue(jen.fitsInCage(3));
    assertFalse(ken.fitsInCage(2));
}
}
```

In the testIsHealthy method of the BoaTest class, assertions were included to verify that the isHealthy method returns true for both Boa objects. Similarly, in the testFitsInCage method, assertions were added to ensure that the fitsInCage method returns the anticipated results for the Boa objects.

```java
import org.junit.Before;
import org.junit.Test;
import static org.junit.Assert.*;

public class BoaTest {

private Boa jen;
private Boa ken;

@Before
public void setUp() throws Exception {
    jen = new Boa("Jennifer", 2, "grapes");
    ken = new Boa("Kenneth", 3, "granola bars");
}

@Test
public void testIsHealthy() {
    assertTrue(jen.isHealthy());
    assertTrue(ken.isHealthy());
}

@Test
public void testFitsInCage() {
    assertFalse(jen.fitsInCage(1)); // cage length less than boa length
    assertTrue(jen.fitsInCage(2)); // cage length equal to boa length
    assertTrue(jen.fitsInCage(3)); // cage length greater than boa length
   
    assertFalse(ken.fitsInCage(2)); // cage length less than boa length
    assertTrue(ken.fitsInCage(3)); // cage length equal to boa length
    assertTrue(ken.fitsInCage(4)); // cage length greater than boa length
}
}
```
In this scenario, the testFitsInCage method of the BoaTest class was modified to include assertions that validate the output of the fitsInCage method for both jen and ken when the cage length is lesser than, equal to, and greater than the length of the boa.

With this enhancement, the testFitsInCage method now becomes more comprehensive as it verifies the behavior of the fitsInCage method for various input values. By testing the method with different inputs, we can ensure that the method works correctly across different scenarios, and this improves the overall robustness and reliability of the code.

```java
public class Boa { private String name; private int length; // the length of the boa, in feet private String favoriteFood;

public Boa(String name, int length, String favoriteFood) {
    this.name = name;
    this.length = length;
    this.favoriteFood = favoriteFood;
}

// returns true if this boa constrictor is healthy
public boolean isHealthy() {
    return this.favoriteFood.equals("granola bars");
}

// returns true if the length of this boa constrictor is
// less than the given cage length
public boolean fitsInCage(int cageLength) {
    return this.length < cageLength;
}

// produces the length of the Boa in inches
public int lengthInInches() {
    return this.length * 12;
}
}
```
The BoaTest class has been updated to include a new method called testLengthInInches(), in addition to the existing testIsHealthy() and testFitsInCage() methods. The new testLengthInInches() method checks that the length of the Boa object is correctly converted from feet to inches.

```java
import static org.junit.Assert.*;
import org.junit.Before;
import org.junit.Test;

public class BoaTest { private Boa jen; private Boa ken;

@Before
public void setUp() throws Exception {
    jen = new Boa("Jennifer", 2, "grapes");
    ken = new Boa("Kenneth", 3, "granola bars");
}

@Test
public void testIsHealthy() {
    assertFalse(jen.isHealthy());
    assertTrue(ken.isHealthy());
}

@Test
public void testFitsInCage() {
    assertTrue(jen.fitsInCage(24));
    assertFalse(jen.fitsInCage(16));
    assertTrue(ken.fitsInCage(36));
    assertTrue(ken.fitsInCage(24));
    assertFalse(ken.fitsInCage(18));
}

@Test
public void testLengthInInches() {
    assertEquals(24, jen.lengthInInches());
    assertEquals(36, ken.lengthInInches());
}
}
```
