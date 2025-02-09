---
title: About
permalink: /about/
layout: single
toc: true
sidebar:
  nav: "sidebar"
---

## Why?

Nothing is more annoying than a unit test that fails without clearly explaining why. More than often, you need to set a breakpoint and start up the debugger to be able to figure out what went wrong. Jeremy D. Miller once gave the advice to "keep out of the debugger hell" and I can only agree with that.

For instance, only test a single condition per test case. If you don't, and the first condition fails, the test engine will not even try to test the other conditions. But if any of the others fail, you'll be on your own to figure out which one. I often run into this problem when developers try to combine multiple related tests that test a member using different parameters into one test case. If you really need to do that, consider using a parameterized test that is being called by several clearly named test cases.

That’s why we designed Fluent Assertions to help you in this area. Not only by using clearly named assertion methods, but also by making sure the failure message provides as much information as possible. Consider this example:

```c#
string accountNumber = "1234567890";
accountNumber.Should().Be("0987654321");
```

This will be reported as:

> Expected accountNumber to be
"0987654321", but
"1234567890" differs near "123" (index 0).

The fact that both strings are displayed on a separate line is not a coincidence and happens if any of them is longer than 8 characters. However, if that's not enough, all assertion methods take an optional explanation (the because) that supports formatting placeholders similar to String.Format which you can use to enrich the failure message. For instance, the assertion

```c#
var numbers = new[] { 1, 2, 3 };
numbers.Should().Contain(item => item > 3, "at least {0} item should be larger than 3", 1);
```

will fail with:

> Expected numbers to have an item matching (item > 3) because at least 1 item should be larger than 3.

## Supported Frameworks and Libraries

Fluent Assertions cross-compiles to .NET Framework 4.7, as well as .NET Core 2.1 and 3.0, .NET Standard 2.0 and 2.1.

Because of that Fluent Assertions supports the following minimum platforms.
*   .NET Core 2.1 and 3.0
*   .NET Framework 4.7 and later
*   Mono 5.4, Xamarin.iOS 10.14, Xamarin.Mac 3.8 and Xamarin.Android 8.0
*   Universal Windows Platform 10.0.16299 and later

Fluent Assertions supports the following unit test frameworks:

*   MSTest2 (Visual Studio 2017, Visual Studio 2019)
*   [NUnit](http://www.nunit.org/)
*   [XUnit2](https://github.com/xunit/xunit/releases)
*   [NSpec](http://nspec.org/)
*   [MSpec](https://github.com/machine/machine.specifications)

## Coding by Example ##
As you may have noticed, the purpose of this open-source project is to not only be the best assertion framework in the .NET realm, but to also demonstrate high-quality code.
We heavily practice Test Driven Development and one of the promises TDD makes is that unit tests can be treated as your API's documentation.
So although you are free to go through the many examples here, please consider to analyze the many [unit tests](https://github.com/fluentassertions/fluentassertions/tree/master/Tests/Shared.Specs).

## Who is behind this project

My name is [Dennis Doomen](https://twitter.com/ddoomen) and I work for Aviva Solutions (in The Netherlands). I maintain a [blog](http://www.continuousimprover.com/) on my everlasting quest for knowledge that significantly improves the way you build your key systems in an agile world. Fluent Assertions is one of those aspects of that.

Notable contributors over the last year include.

* [Adam Voss](https://github.com/adamvoss)
* [Jonas Nyrup](https://github.com/jnyrup)
* [Artur Krajweski](https://github.com/krajek)

The [Fluent Assertions logo](./logo/fluent_assertions.svg) was created by

* [IUsername](https://github.com/IUsername)

If you have any comments or suggestions, please let us know via [twitter](https://twitter.com/search?q=fluentassertions&src=typd), through the [issues](https://github.com/dennisdoomen/FluentAssertions/issues) page, or through [StackOverflow](http://stackoverflow.com/questions/tagged/fluent-assertions).

## Versioning

The version numbers of Fluent Assertions releases comply to the [Semantic Versioning](http://semver.org/) scheme. In other words, release 1.4.0 only adds backwards-compatible functionality and bug fixes compared to 1.3.0. Release 1.4.1 should only include bug fixes. And if we ever introduce breaking changes, the number increased to 2.0.0.

## What do you need to compile the solution?

* Visual Studio 2019 16.9+ or Jetbrains Rider and Build Tools 2017
* Windows 10
* .NET Framework 4.7 SDK and .NET 5.0 SDK (check [global.json](https://github.com/fluentassertions/fluentassertions/tree/develop/global.json) for the current minimum required version)
