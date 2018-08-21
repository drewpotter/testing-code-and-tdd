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
* Run the spec;
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


## Create a class

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


## Slide 2

```js
var a = 1;
```
