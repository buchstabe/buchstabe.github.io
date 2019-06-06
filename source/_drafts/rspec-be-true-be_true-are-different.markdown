---
author: Andrei Beliankou
lang: en
permalink: /en/notebook/:year/:month/:title.html
layout: post
title: "RSpec be true and be_true are different"
date: 2013-02-24 18:39
comments: true
categories: Ruby Deployment
---

source: https://bengribaudo.com/blog/2014/01/17/2674/rspec-be-true-be_true-are-different

RSpec’s be true and be_true look deceptively similar. In fact, their naming suggests that they might be synonyms for the same assertion. Can the two clauses be used interchangeably to produce the same effect? No!

Both check trueness but from different perspectives. be true checks whether the compared-against value is true: “Does the value literally equal true?” be_true asserts that the test value evaluates to true: “Is the value truthy?” be false and be_false are the respective inverse match clauses.

While be true‘s name literally describes what it asserts, be_true‘s name is arguably ambiguous. To prevent future confusion, be_true will be renamed be_truthy and be_false will become be_falsey in the upcoming RSpec 3.0 release.
be true/be false

Asserts that the tested-against expression literally equals true or false (respectively).
1
2
3
4
5
6
7

it { expect(true).to be true }      # passes
it { expect("abc").to be true }     # fails
it { expect(nil).to be true }       # fails

it { expect(false).to be false }    # passes
it { expect("abc").to be false}     # fails
it { expect(nil).to be false}       # fails
be_true/be_false (soon to be be_truthy/be_falsey)

Asserts that the tested-against expression evaluates to true or false (respectively).
1
2
3
4
5
6
7

it { expect(true).to be_true }      # passes
it { expect("abc").to be_true }     # passes
it { expect(nil).to be_true }       # fails

it { expect(false).to be_false }    # passes
it { expect("abc").to be_false}     # fails
it { expect(nil).to be_false }      # passes
