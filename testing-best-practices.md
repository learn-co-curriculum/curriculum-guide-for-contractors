Testing: Best Practices
---

## Rails

### Don't use `assigns` in controller tests

(Thanks, @loganhasson)

For example:

``` ruby
let(:author) { Author.create!(name: "H. Jeff", email: "jeff@sbahj.info") }
describe "creating an invalid author" do
  before { post :create, email: author.email }

  it "does not create" do
    expect(assigns(:author)).to be_new_record
  end
end
```

creates failure output like this:

``` bash
Failure/Error: expect(assigns(:author)).to be_new_record
  expected nil to be a new record, but was persisted
Instead, it could be written more like this to get better failure output:
```

``` ruby
let(:email) { 'test@example.com' }

it "does not create" do
  expect(Author.find_by(email: email)).to be_nil
end
```

Similarly, rather than checking to see if attributes on assigns(:some_model) has been modified on update actions/created on create actions/etc, check the database to see if the correct data has/has not been written.


### Testing Views

(Courtesy of @jmburges)

Generally, avoid view specs unless you're testing something incredibly lightweight. Instead, follow the guidelines in this post: http://ruby-journal.com/how-to-write-rails-view-test-with-rspec/

### Testing Puts

(Thanks, @aviflombaum)

#### Testing `puts` Outside of a Method

The best way to test the usage of `puts` outside the context of a method is to `load` the file that will make a call to `puts` within an `it` block and `expect` `$stdout` `to` `receive` a call to `puts` `with` your desired output.

#### Example: Testing a CLI Welcome Message

If you were developing a lesson that requires the student's program to print out a message at the start, independent of any initialization method call or object instantiation, as in the example of building a simple program that when run, simply prints `"Hello, World!", the preferred pattern is as follows:

File: `spec/hello_world_spec.rb`
```ruby
describe "hello_world.rb" do
  it 'prints "Hello, World!" when run or loaded' do
    expect($stdout).to receive(:puts).with("Hello, World!")

    load './lib/hello_world.rb'
  end
end
```

The solution file would look like:

File: `lib/hello_world.rb`
```ruby
puts "Hello, World!"
```

#### Testing `puts` within a Method

When the student is required to build a method that upon evocation should output a string, the pattern to use is:

1. require the file with the method definition in the test suite,
2. set the expectation of `$stdout` `to` `receive` `puts` `with` your desired string.
3. Evoke the method.

#### Example: Testing a `puts` within a Method

If you were to develop a lesson that required the student to define a method that prints a message dependent upon an argument or external data, use this pattern.

The student must build a `say_hello` method that accepts an argument of `name` and must output "Hi #{name}!".

File: `spec/say_hello_spec.rb`
```ruby
require_relative '../lib/say_hello'

describe "#say_hello" do
  it 'prints "Hello <NAME>" for whatever name is passed as an argument' do
    expect($stdout).to receive(:puts).with("Hello Kent Beck!")
    say_hello("Kent Beck")
  end
end
```

The solution:

File: `lib/say_hello.rb`
```ruby
# Build your say_hello method here
def say_hello(name")
  puts "Hello #{name}"
end
```

### Testing Multiline Puts

(Thanks again, @aviflombaum)

When you want to allow the student to either have several calls to puts for each line or iteration or to concatnate a larger string and display it via a single call to puts, a good way to test that during entirety of the program or method runtime, puts was correctly evoked to produce a desired output, this works very well:

```ruby
require_relative '../lib/display_board'

def capture_puts
  begin
    old_stdout = $stdout
    $stdout = StringIO.new('','w')
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end


describe '/lib/display_board.rb' do
  it 'defines a method display_board' do
  end

  it 'the #display_board method prints out a tic tac toe board' do
    output = capture_puts{ display_board }

    expected_output  = "   |   |   \n"
    expected_output += "-----------\n"
    expected_output += "   |   |   \n"
    expected_output += "-----------\n"
    expected_output += "   |   |   \n"

    expect(output).to eq(expected_output)
  end
end
```

Note that this will fail if the student is using non-standard returns (`\r\n` or something). Students should, in that case, probably reconfigure their text editors — that's a recipe for a disaster if they keep doing it, and not a problem with the test itself.

Solution:

```ruby
def display_board
  # puts <<-DOC
  #   |  |
  # --------
  #   |  |
  # --------
  #   |  |
  # DOC

  puts "  |  |
--------
  |  |
--------
  |  | "

  # puts "  |  |  "
  # puts "--------"
  # puts "  |  |  "
  # puts "--------"
  # puts "  |  || "
end
```

Every style of puts in that method will pass the captured output call.

Otherwise you have to spec individual calls to puts or a single combined call to puts. This allows flexibility of implementation but clarity in desired outcome.

### Testing that a file defined a local variable outside of a method or a enclosing scope

(Thanks again, @aviflombaum.)

#### Using static analysis ####

Example:
```ruby
describe "local variables" do

  let(:right_answers) { ["greeting = \"Hello World\"", "greeting=\"Hello World\"", "greeting = \'Hello World\'", "greeting=\'Hello World\'"] }

  before(:each) do
    @content = File.open("variable.rb", "r") { |f| content = f.read }
  end

  it "defined a local variable called greeting and set it equal to 'Hello World'" do
    expect(right_answers.any? { |answer| @content.match(answer) }).to eq(true)
  end

  it "should not be an instance variable" do
    expect(@content).to_not include("@")
  end

  it "should not be an global variable" do
    expect(@content).to_not include("$")
  end
end
```

Solution File: `variable.rb`
```ruby
 greeting = 'Hello World'
```

#### Using binding and eval ####

Say you want to test that a file simply defines a local variable. You can do that with static analysis of the file, basically reading it as text and looking for a pattern in the string that looks like variable assignment. Works well, but it's weird and not honest to what the code is trying to do. This works too:

File: `spec/board_spec.rb`
```ruby
require 'pry'

describe "lib/board.rb" do
  it 'defines a local variable `board`' do
    file_scope = binding
    file_scope.eval(File.read("./lib/board.rb"))
    board = file_scope.local_variable_get("board")

    expect(board).to_not be_nil
  end

  it '`board` is set to an array' do
    file_scope = binding
    file_scope.eval(File.read("./lib/board.rb"))
    board = file_scope.local_variable_get("board")

    expect(board).to be_a(Array)
  end

  it '`board` is an array with 9 elements' do
    file_scope = binding
    file_scope.eval(File.read("./lib/board.rb"))
    board = file_scope.local_variable_get("board")

    expect(board.size).to eq(9)
  end
end
```

Solution File: `lib/board.rb`
```ruby
board = Array.new(9)
```

#### Which Pattern to Use? ####

To me it's all about the RSpec feedback and error messages.

Using Bindings:

```
1) lib/board.rb defines a local variable `board`
     Failure/Error: expect(board).to_not be_nil
       expected: not nil
            got: nil
     # ./spec/board_spec.rb:9:in `block (2 levels) in <top (required)>'
```

Static Analysis:
```
  1) local variables defined a local variable called greeting and set it equal to 'Hello World'
     Failure/Error: expect(right_answers.any? { |answer| @content.match(answer) }).to eq(true)

       expected: true
            got: false

       (compared using ==)
     # ./spec/variable_spec.rb:11:in `block (2 levels) in <top (required)>'
```

I think `binding` lends itself to better feedback.
