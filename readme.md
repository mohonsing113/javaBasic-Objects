# Overview

This repository is a part of the Java language training plan. Please read the following guidelines before start.

# Getting Start

## Basic Principals

Each repository contains a gradle java project with a number of unit tests. The initial state of all unit tests are *FAILED*. So the aim is to correct the failed test. Please follow the following steps to get the best experience:

* Read the test code and try to understand what it says.
* Trying to fix the test **WITHOUT RUNNING**. This is very important. Because once you run the test, you may find the failure message of the test telling you the expected result. That means you may lose the chance to figure it out by yourself. Note that you should **ONLY** be able to modify code within the **TODO AREA**. The code outside the **TODO AREA** is **NOT** changable.
* Run the test to examine if the fix is correct.
* Answer the following 4 questions after the test is passed.

The 4 questions are:

1. What is the knowledge point of the test? Where is the offical document to the knowledge point?
1. Why the test failed at first?
1. Why you corrected the test that way?
1. Do you have further questions on this knowledge point?

## Example

Let's take a look at an example:

```java
@Test
void should_pass_by_value() {
  int value = 5;

  tryingToUpdateValue(value);

  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 0;
  // --end-->

  assertEquals(expected, value);
}
```

First, read the test. From the title and code we can know that the test what to examine the behavior when passing an argument. We are not sure what `tryingToUpdateValue` does, so we can jump into its implementation:

```java
private static void tryingToUpdateValue(int value) {
  value += 2;
}
```

Now we have got the full context of the test. The argument is passed by value so the integer will be copied when passing into `tryingToUpdateValue`. Thus the value from the caller site will not change.

Notice that the todo area is in the test method. So we can modify codes within the todo area to pass the test:

```java
  // TODO: please modify the following code to pass the test
  // <--start
  final int expected = 5;
  // --end-->
```

Please note that not all todo areas are located in test method. And some todo area may have further restrictions, for example:

```java
  // TODO: You should not write concrete number here. Please find a property or constant instead.
  // <!--start
  final int maximumSymbol = 0;
  final int minimumSymbol = 0;
  // --end-->
```

The hint indicates that we should not write concrete number here. So I should not write `3` or `0xffffffff`, but write symbol (e.g. `Integer.MAX_VALUE`).

## Running Test

You could run unit tests with the help of IntelliJ. But it is also possible to run unit test via command line: `./gradlew build`.

If you just want to build your code without running test. Please use `./gradlew build -x test
`
## Summary

* should_customize_exception(), should_customize_exception_continued()
1. Try to handle exception and constructor
1. The constructor of the exception is not set
1. Change the exception constructor
1. NO

* should_be_careful_of_the_order_of_finally_block()
1. Study the behavior of finally block
1. It expect a max int
1. change the expected to 0 which is the result of finally block
1. NO

* should_use_the_try_pattern() 
1. Use a catch block for the try block
1. It expect empty
1. Catch the exception if cannot get isClosed. close it and assume it is closed
1. NO

* should_call_closing_even_if_exception_throws() 
1. Use a catch block for the try block
1. It expect empty
1. Catch the exception if cannot get isClosed. close it and assume it is closed
1. NO

* should_be_derived_from_object_class()
1. Inheritance of all class
1. it expect null
1. it is object, so = Object.class
1. NO

* should_call_super_class_constructor(), should_call_super_class_constructor_continued(), should_call_super_class_constructor_more(), should_call_super_class_methods(), should_not_make_you_confused, should_not_make_you_confused_2
1. Call superclass method
1. it expect null
1. Get String from superclass as expected result
1. NO

* should_call_most_derived_methods()
1. Call the most derived method if same method appear in super class and itself
1. it expect null
1. get String from most derived method as expected result
1. NO

* should_use_instance_of_to_determine_inheritance_relationship()
1. same instance if inheritance relationship
1. expected optional.empty
1. all true due to inheritance relationship
1. NO

* should_use_instance_of_only_in_inheritance_relationship
1. not same instance if not inheritance relationship
1. expected optional.empty
1. Long has no inheritance relationship with integer, so false
1. NO

* should_write_perfect_equals_1, should_write_perfect_equals_2, should_write_perfect_equals_3, should_write_perfect_equals_6
1. == operator only check reference not logically equals
1. methods not implemented
1. implemented a method that check both variables are equal
1. NO

* should_write_perfect_equals_4, should_write_perfect_equals_5
1. exception handling
1. methods not implemented
1. add try catch block in equals()
1. NO

* should_write_perfect_equals_7
1. create hascode
1. methods not implemented
1. implemented a method that return hashCode create by its own fields
1. NO

* should_get_method_name_in_stack_frame
1. get mehod name
1. methods not implemented
1. get the name of method and class
1. NO

* should_point_to_the_same_object
1. object refence behavior
1. expected empty
1. they are same object
1. NO

* should_point_to_different_object
1. object refence behavior
1. expected empty
1. they are not same object even the data inside are same, so = false
1. NO

* should_initialized_to_default_value
1. instance behavior
1. expected setted value
1. they have not same at instance so the getter will return null / 0
1. NO

* should_pass_by_value
1. parameter behavior
1. expected 0
1. primitive type pass in method will not affect it original
1. NO

* should_pass_by_value
1. parameter behavior
1. expected null
1. object type pass in method will be the reference and will be affected
1. NO

* should_modify_internal_state
1. using a method can update an object internal state outside
1. expected null
1. copy the new string as result
1. NO

* should_choose_method_at_compile_time, should_choose_the_most_specific_overload
1. parameter behavior
1. expected null
1. method is chosen based on parameter type and number of parameter
1. NO

* should_calling_another_constructor
1. constructor behavior
1. expected null
1. constructor can be mutiple as methods too, same chosing constructor logic applied constructor
1. NO

* should_get_initialization_ordering
1. order of init
1. expect []
1. input the correct order
1. NO

* should_get_message_of_var_length_parameters, should_get_message_of_var_length_parameters_2
1. usage of Object... args parameter type compared to new Object[]
1. expect null
1. input the builder result
1. NO

