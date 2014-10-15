# Blog Post Notes

Are factories making you lose the design benefits of TDD?

## What's wrong with factories
- They're too easy
- They get slow

## Mocking/stubbing
- forces you to state your dependencies
- very clear what parts of things you are using
- encourages you to push logic elsewhere
- use example with adding 4 fields on another object

## What's wrong with mocking/stubbing?
- interface drift (rspec helps us with instance_double("ClassName"))
- return values of stubbed methods
	- how do we know that the method we stubbed actually ever returns a compatible value?
	- stubbing/mocking supposes a lot of knowledge about what is being stubbed and mocked, however, if the thing being stubbed/mocked ever changes, it is almost impossible to know all the dependencies that should be changed.

## How can we know that our return values are good?
- We could investigate the code and try to determine if our stubbed value is a possible return value for the method.
	- This would probably be hard, and slow
- What about through other tests? You already wrote tests for the stubbed method right? (or you will in future).
	- If the tests assert the types/behaviours of return values, then in tests where we stub said method, we should be able to assert that our stubbed value is on of the values that other tests assert is possible.


------------------------------------


# Early Notes

Given that we stub a method `:method_name` with a return value "value", we should be able to look up the tests for `:method_name`, and assert that those tests ever return a string value (or whatever type we stubbed).

Going further, it could assert that the methods we call in the test where we stub `:method_name`, are methods that are stated as existed in the test for method name.

Basically we are checking that the return values conform to a certain interface.


-------------------------------------


# Research

- [Magic Tricks of Testing](http://www.youtube.com/watch?v=URSWYvyc42M) by Sandi Metz
