## Testing code and TDD
_Andrew Potter_

Why it is so vital. Best practices and how to improve your code using this methodology.


## What is testing?

It may seem obvious. Testing is where we test our software to see if it works properly.


## Why we test ?

* It helps us to find errors in our code, especially when refactoring.


## Why we test ?

* Living documentation for your code. How it works and how to invoke your code.


## Why we test ?

* To cover many different scenarios in an automated fashion which will take hours to test manually.


## TDD: A feedback loop

* Test-driven development; a feedback loop,
* Before writing a single line of code have a failing test.


## TDD; Don't think of the code!

* Don't think of the code in your head before writing the test


## TDD; minimal code

* Once you have written the test, then write the minimal code needed to pass the test.


## TDD; design emerges

* Finally you will have the design emerge through the refactoring of the code.


## TDD; Remove duplication

This method of development allows us to continually refactor until all duplication is removed.


## Testing frameworks

Many testing frameworks exist, here I will discuss a few of these.


## Testing frameworks; Ruby
* RSpec; BDD
* Cucumber; plain language
* Minitest; used by Rails


## Testing frameworks; JavaScript
* Mocha
* Chai


## Testing frameworks; Solidity
* Truffle Suite


## Testing frameworks; Elixir
* ExUnit


## Let's look at RSpec

* Install RSpec
* Write a spec
* Run the spec
* Drive development of our app.


## Install RSpec

```
gem install rspec
```


## Write a spec

```
RSpec.describe something do

end
```


## Write a spec

hello_world_spec.rb
```
RSpec.describe HelloWorld do

end
```


## Run the spec

To run this spec we can do this, from the same folder:
```
rspec hello_world_spec.rb
```


## Output

```
An error occurred while loading ./hello_world_spec.rb.
Failure/Error:
  RSpec.describe HelloWorld do

  end

NameError:
  uninitialized constant HelloWorld
```


## Why?

Does anyone who doesn't work with Ruby every day want to guess why this won't work?


## Test Failure

This is because we have not defined the `HelloWorld` class yet.


## The HelloWorld class

Create a file in the same folder:
`hello_world.rb`


## The HelloWorld class

```
class HelloWorld

end
```


## Re-run the test

```
An error occurred while loading ./hello_world_spec.rb.
Failure/Error:
  RSpec.describe HelloWorld do

  end

NameError:
  uninitialized constant HelloWorld
```


## The same test failure

It is clear that the test is failing again.
The spec cannot find the the `HelloWorld` class.


## To fix this

Add to the top of the spec:
```
require_relative 'hello_world'

```


## Rerun the spec

```
Finished in 0.00024 seconds (files took 0.26015 seconds to load)
0 examples, 0 failures
```
No errors


## Let's build the class

Next we will build the test and the class with a method to output "Hello World".


## TDD; Our expectations?

* We want a method which will output "Hello World"
* Running this method will return "Hello World"


## TDD; Write our test in our spec

```
RSpec.describe HelloWorld do

  it "should output 'Hello world'" do
    output = HelloWorld.bonjour
    expect(output).to eq("Hello world")
  end

end

```


## TDD; Run the test

```
F

Failures:

  1) HelloWorld should output 'Hello world'
     Failure/Error: output = HelloWorld.bonjour

     NoMethodError:
       undefined method `bonjour' for HelloWorld:Class

```


## TDD; Create the method

So now create the `bonjour` method inside the `HelloWorld` class.

Remember we are doing the minimum amount of work for each step.


## TDD; Add the method

```
class HelloWorld
  def self.bonjour

  end
end
```
We use `self` because it is a class method.


## TDD; Re-run the test

```
F

Failures:

  1) HelloWorld should output 'Hello world'
     Failure/Error: expect(output).to eq("Hello world")

       expected: "Hello world"
            got: nil

       (compared using ==)
```


## TDD; Add "Hello world"

```
class HelloWorld
  def self.bonjour
    "Hello world"
  end
end
```


## TDD; Rerun the test

```
Finished in 0.00715 seconds (files took 0.18603 seconds to load)
1 example, 0 failures
```


## TDD; Summary
* We have gone through the basics of using TDD.
* TDD is a feedback loop.
* TDD improves code quality.


## 10 principles for testing
This primarily focuses on TDD or Test Driven Development when developing projects.


## 10 principles for testing
1) Acceptance criteria; you will normally have a set of features which you need to implement for certain functionality to exist. These correspond to the acceptance criteria for the test you are writing.


## 10 principles for testing
2) Living documentation; if you want to become familiar with a new project you have not used before you can familiarise yourself with the tests. Therefore tests should be written in such a way as to be clear to read and understand. This leads on to the next point;


## 10 principles for testing
3) Use clear test descriptions. It is vital to provide clear test descriptions. For example;

```
  test "html request to /sites returns a list of the users sites" do
    sign_in @user
    get sites_path

    assert_equal 2, @controller.instance_variable_get("@sites").count
  end
```
Here we are clearly naming the test with it's purpose and what it is testing.


## 10 principles for testing
4) There are many types of tests; this includes models, controllers, systems and integrations tests.
* _model_ tests are pretty straightforward and as you would expect they test your models.
* _controller_ tests, similarly, are straightforward and provide functional testing for your controllers.
* _system_ tests through the use of Capybara allow you to test user interaction with your Rails app.
* _integration_ tests are used to test how particular parts of your application interact.


## 10 principles for testing
5) DRY, Don't Repeat Yourself - when you are setting up a variable multiple times across all tests within the same test Ruby file, you can use a `setup` method to remove additional repeated lines of code and only write that line once. For example;

```
  setup do
    @user = create(:user)
  end
```

This can also apply when logging in the user if they are supposed to be logged in for example in all tests of the same Ruby test file.


## 10 principles for testing
6) Refactoring with confidence; when you have thorough testing in place you can confidently refactor your code knowing that this will not break things provided that you have good test coverage.


## 10 principles for testing
7) Small steps; TDD enables us to make small steps writing our code - for example less than 10 lines of code - before re-running our tests to check the code we have added to the project. This is much better than adding large amounts of code only to find problems later.


## 10 principles for testing
8) Before writing a single line of code have a failing test; This will help you to always follow the TDD approach by starting out always with this method and this also links to the next point.


## 10 principles for testing
9) Don't think of the code in your head before writing the test; Once you have written the test, then write the minimal code needed to pass the test. Finally you will have the design emerge through the refactoring of the code.


## 10 principles for testing
10) Remove duplication; This method of development allows us to continually refactor until all duplication is removed.


## TDD; Questions
* Any questions?
* Thanks for watching this presentation!
* Contact: andrew.potter [at] unep-wcmc.org
