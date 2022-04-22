---
layout: post
title:  "C# Pattern Matching"
date:   2022-04-21 09:00:00 +0100
categories: .Net
---

* Since `Pattern matching` has been added in C# 7.0, it has evolved from strength to strength in every version of the language since.
* `is` and `switch` are the 2 keywords that enable to apply a pattern along with relational `<, >, <=, >=` and logical `not, and, or` operators.
* It allows to build powerful yet succint logic in an elegant way.
* From personal experience, it is easy to get carried away and pack several scenarios in a small space however adopting a `TDD` approach covering each scenario will guard against regression and make it easy to control changes.

#### Introduced in C# 7.0

| Pattern      | Description |
| ----------- | ----------- |
| Declaration      | Defines an expression that gets evaluated at runtime and the expression result gets assigned to a variable if the matching criteria is true     |
| Constant   | An expression gets evaluated and compared  a constant        |
| var   | An expression gets evaluated and result is assigned to a declared variable    |


#### Introduced in C# 8.0

| Pattern      | Description |
| ----------- | ----------- |
| Property      | Evaluates an expression and checks if the properties and fields match nested patterns    |
| Positional   | Called as such because the position of the property in a deconstructed result matters when an expression is evaluation. Can also do tuple comparison. |
| Discard   | Uses the _ variable, usually as a default handling, null check or where the result of the evaluated expression is not used ultimately   |

#### Introduced in C# 9.0

| Pattern      | Description |
| ----------- | ----------- |
| Type      | Evaluate an expression and check the runtime type   |
| Relational    | Use relational operators in a switch statement to compare with a specified constant |
| Logical   | Evaluates an expression and use logical operators to compare with one or more patterns |

