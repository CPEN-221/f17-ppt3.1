CPEN 221 / Fall 2017

Programming Proficiency Test
=========

November 7, 2017

## General Instructions

+ You have 72 minutes (1h 12m) to complete the assigned tasks.
+ Take your time to read the question.
+ Skeleton code can be obtained by cloning this repository. Add JUnit to your build path in Eclipse.
+ Best of luck!

## Submission Instructions

+ Submit your work to the Github classroom repository that was created for your.
+ **Do not alter the directory/folder structure. You should retain the structure as in this repository.**
+ Do not wait until the last minute to push your work to Github. It is a good idea to push your work at intermediate points as well. _I would recommend that you get your Git and Github workflow set up at the start._

## Honour Code

By submitting your work to Github you agree to the following:

+ You did not consult with any other person in completing the examination.
+ You did not aid any other person in the class in completing their examination.
+ If you consulted any external sources, such as resources available on the World Wide Web, in completing the examination then you have cited the source. (You do not need to cite class notes or Sun/Oracle Java documentation.)
+ You are not aware of any infractions of the honour code for this examination.

> Violations of this honour code will be treated as a case of academic misconduct and will dealt with under UBC policies governing such issues. A consequence of this may be to nullify this exam for everyone that submits work for grading!

## Question: Odd-Even Bag
> The skeleton source code for this question is in the package `oddevenbag`. You have to implement the required method in the class `OddEvenBag`. You may import the provided code as a Gradle project in Eclipse.

An `OddEvenBag` allows us to store `int`s (including duplicates) and perform some useful operations on the collection of `int`s.

Here are the essential operations that an `OddEvenBag` supports:

1. **Creators**
	1. Create an empty `OddEvenBag`
	2. Create an `OddEvenBag` using an array of `int`s as initial values
2. **Mutators**
	1. Add a given `int`
	2. Remove one occurrence of a given `int`
	3. Increment: increase the value of each entry by 1
	4. Decrement: decrease the value of each entry by 1
3. **Observers**
	1. Check if an `int` is in the `OddEvenBag`
	2. Return a count of the number of occurrences of an `int` in the bag
	3. Return the sum of the elements in the bag
	4. Verify equality: two `OddEvenBags` are equal if and only if they contain an identical quantity of odd numbers and an identical quantity of even numbers (the specific values do not matter here)
	5. A suitable hash code operation

### Specifications

```
// Create an empty OddEvenBag
OddEvenBag()

// Create an OddEvenBag using the elements in the provided array
// requires: seedArray is not null
OddEvenBag(int[] seedArray)

// add x to the OddEvenBag
add(int x)

// remove x from the OddEvenBag
// if x does not exist in the Bag then do nothing
void remove(int x)

// increment each value in the OddEvenBag by 1
void increment()

// decrement each value in the OddEvenBag by 1
void decrement()

// return true if this OddEvenBag contains x
// and false otherwise
boolean contains(int x)

// count the occurrences of x in the OddEvenBag
int getCount(int x)

// return the sum of the values in the OddEvenBag
long sum()
```

Although not listed above, `equals()` and `hashCode()` should be implemented.

### Test Cases

```java
@Test
public void test1() {
	OddEvenBag oeb = new OddEvenBag();
	oeb.add(10);
	assertTrue(oeb.contains(10));
	assertEquals(10, oeb.sum());
}

@Test
public void test2() {
	OddEvenBag oeb = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	assertTrue(oeb.contains(5));
	assertEquals(21, oeb.sum());
}

@Test
public void test3() {
	OddEvenBag oeb = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	oeb.increment();
	assertEquals(27, oeb.sum());
}

@Test
public void test4() {
	OddEvenBag oeb = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	oeb.decrement();
	assertEquals(15, oeb.sum());
}

@Test
public void test5() {
	OddEvenBag oeb1 = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	OddEvenBag oeb2 = new OddEvenBag(new int[] { 12, 14, 18, 3, 9, 11 });
	assertTrue(oeb1.equals(oeb2));
	assertTrue(oeb2.equals(oeb1));
	assertTrue(oeb1.hashCode() == oeb2.hashCode());
}

@Test
public void test7() {
	OddEvenBag oeb1 = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6 });
	OddEvenBag oeb2 = new OddEvenBag(new int[] { 1, 3, 6, 2, 4, 6 });
	assertTrue(!oeb1.equals(oeb2));
	assertTrue(!oeb2.equals(oeb1));
}

@Test
public void test8() {
	OddEvenBag oeb1 = new OddEvenBag(new int[] { 1, 3, 5, 2, 4, 6, 8 });
	OddEvenBag oeb2 = new OddEvenBag(new int[] { 1, 3, 7, 2, 4, 6, 10 });
	oeb1.increment();
	assertTrue(!oeb1.equals(oeb2));
	assertTrue(!oeb2.equals(oeb1));
}

@Test
public void test9() {
	OddEvenBag oeb = new OddEvenBag();
	String s = "abc";
	assertTrue(!oeb.equals(s));
}
```

## What Should You Implement / Guidelines

+ You should implement all the methods that are indicated with `TODO`.
+ Passing the provided tests is the minimum requirement. Use the tests to identify cases that need to be handled. Passing the provided tests is *not sufficient* to infer that your implementation is complete and that you will get full credit. Additional tests will be used to evaluate your work. The provided tests are to guide you.
+ You can implement additional helper methods if you need to but you should keep these methods `private` to the appropriate classes.
+ You do not need to implement new classes.
+ You can use additional standard Java libraries by importing them.
+ Do not throw new exceptions unless the specification for the method permits exceptions.

## Answers to FAQs

#### Can I consult Java documentation and other Internet-based sources?

Yes, you can. The point of this test is not to demonstrate mastery over syntax but that you can solve a problem in a reasonable amount of time with reasonable resources.

*If you find useful information online outside the official Java documentation and the course material, you must cite the source. You should do so by adding comments in your source code.*

Naturally you are expected to adhere to all of the course and UBC policies on academic integrity.

#### Isn't one hour too short to produce a working implementation?

The questions are straightforward, and these are not very different from what one might sometimes encounter on a job interview (for example). The difference is that you get less time during an interview (10-15 minutes) with no access to additional resources. So the time allotted is reasonable in that regard and I am expecting that everyone will be able to clear this bar. The goal is that it is possible to say, at a minimal level, what everyone who completes this course can achieve.

#### Why am I not guaranteed full credit if my implementation passes all the provided tests?

It is easy to develop an implementation that passes the provided tests and not much else. A good-faith implementation that passes all the provided tests is very likely to pass other tests too.
