---
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "The Safe Navigation Operator in Ruby"
# date: 2019-02-07 15:30:01 +0100
comments: true
categories: Ruby
---

<-- Origin: http://mitrev.net/ruby/2015/11/13/the-operator-in-ruby/

-->

The most interesting addition to Ruby 2.3.0 is the Safe Navigation Operator(`&.`). A similar operator has been present in C# and Groovy for a long time with a slightly different syntax - `?.`. So what does it do?

## Scenario

Imagine you have an account that has an owner and you want to get the owner’s address. If you want to be safe and not risk a nil error, you would write something like the following:

``` ruby
if account && account.owner && account.owner.address
  # ...
end
```
This is really verbose and annoying to type. ActiveSupport includes the try method which has a similar behaviour (but with few key differences that will be discussed later):

``` ruby
if account.try(:owner).try(:address)
  # ...
end
```
It accomplishes the same thing - it either returns the address or nil if some value along the chain is nil. The first example may also return false if, for example, the owner is set to false.

## Using the safe navigation operator (`&.`)

We can rewrite the previous example using the safe navigation operator:

``` ruby
account&.owner&.address
```
The syntax is a bit awkward but I guess we will have to deal with it because it does make the code more compact.

## More examples

Let’s compare all three approaches in more detail.

account = Account.new(owner: nil) # account without an owner

account.owner.address
# => NoMethodError: undefined method `address' for nil:NilClass

account && account.owner && account.owner.address
# => nil

account.try(:owner).try(:address)
# => nil

account&.owner&.address
# => nil

No surprises so far. What if owner is false (unlikely but not impossible in the exciting world of shitty code)?

account = Account.new(owner: false)

account.owner.address
# => NoMethodError: undefined method `address' for false:FalseClass `

account && account.owner && account.owner.address
# => false

account.try(:owner).try(:address)
# => nil

account&.owner&.address
# => undefined method `address' for false:FalseClass`

Here comes the first surprise - the &. syntax only skips nil but recognizes false! It is not exactly equivalent to the s1 && s1.s2 && s1.s2.s3 syntax.

What if the owner is present but doesn’t respond to address?

account = Account.new(owner: Object.new)

account.owner.address
# => NoMethodError: undefined method `address' for #<Object:0x00559996b5bde8>

account && account.owner && account.owner.address
# => NoMethodError: undefined method `address' for #<Object:0x00559996b5bde8>`

account.try(:owner).try(:address)
# => nil

account&.owner&.address
# => NoMethodError: undefined method `address' for #<Object:0x00559996b5bde8>`

Oops, the try method doesn’t check if the receiver responds to the given method. This is why it’s always better to use the stricter version of try - try!:

account.try!(:owner).try!(:address)
# => NoMethodError: undefined method `address' for #<Object:0x00559996b5bde8>`

## Pitfalls

Be careful when using the `&.` operator and checking for `nil` values. Consider the following example:

nil.nil?
# => true

nil?.nil?
# => false

nil&.nil?
# => nil

As Joeri Samson pointed out in the comments, this section is actually wrong - I mistakenly used ?. instead of &.. But I still think that the last example is confusing and nil&.nil? should return true.
Array#dig and Hash#dig

The #dig method is, in my opinion, the most useful feature in this version. No longer do we have to write abominations like the following:

``` ruby
address = params[:account].try(:[], :owner).try(:[], :address)

# or

address = params[:account].fetch(:owner) { {} }.fetch(:address)
```

We can now simply use Hash#dig and accomplish the same thing:

``` ruby
address = params.dig(:account, :owner, :address)
```

# Final words

I really dislike dealing with nil values in dynamic languages (check my previous posts) and think the addition of the safe operator and the dig methods are really neat.
