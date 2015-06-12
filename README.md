[![Build Status](https://travis-ci.org/fbonetti/method_hooks.svg?branch=master)](https://travis-ci.org/fbonetti/method_hooks)

# MethodHooks

Allows you to add `before`, `around`, and `after` callbacks to **any** method.

> Fork Addition : We highly recommend you do NOT fork our fork of the method_hooks gem.  
We are researching this gem for our possible use and so this respository can change rapidly or disappear.  
Any and all improvements we can see to make will be pushed to the original respository at [fbonetti/method_hooks](https://github.com/fbonetti/method_hooks) , and so those are the codes you want to be looking at and using if you like this gem.

> **Unanswered Questions** :

> Before method_hooks is used, you could add these callbacks only to : ( what were limitations before method_hooks ).  
After method_hoods is used, you can add these callback to ANY Ruby method.  Yes, it is a wild claim making this gem valuable indeed.

> The first question this poses is, what were limitations before method_hooks ?  
What methods could not sustain a callback hook ?  
Why ? 

> Before method_hooks is used, you cannot run a callback on a method such as, `bad = Mybad.example` , if that is correct ?? because why ???

> After method_hooks is used, you can run a callback on `good = Good.example` because method_hooks will .. do what ?? provide a wrapper ??? where is the wrapper ? or other-named active code that hooks onto any PORO. (plain old Ruby objects)

> The method_hooks gemm methods can benefit our app in what way ? After I figure that out, I will explain a few use cases here.

> We now return to Original Material untouched by us.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'method_hooks'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install method_hooks

## Usage

```ruby
class Model
  extend MethodHooks

  before :save do
    puts 'before'
  end

  around :save do |method|
    puts 'before_around'
    method.call
    puts 'after_around'
  end

  after :save, :foo do
    puts 'after'
  end

  def save
    puts 'save'
  end

  def foo
    puts 'foo'
  end

end

model = Model.new
model.save
model.foo

=begin

Outputs the following:

before
before_around
save
after_around
after
foo
after

=end
```

## Contributing

1. Fork it ( https://github.com/[my-github-username]/method_hooks/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
