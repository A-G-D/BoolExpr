# API Reference

Back to: [Table of Contents](index.md)

<br/>

## Variables

The following variables are used for manual BoolExpr construction (see [Manually Constructed BoolExpr](2_creating-expressions.md/#manually-constructed-boolean-expressions)).

| Name | Type | Description |
|---|---|---|
| ```BoolExpr.DEF``` | integer | Constructed BoolExpr evaluates to true when [EF](99999_glossary.md) returns true |
| ```BoolExpr.NOT``` | integer | Constructed BoolExpr evaluates to true when EF returns false |
| ```BoolExpr.AND``` | integer | Constructed BoolExpr evaluates to true when both the left EF and right EF both return true |
| ```BoolExpr.OR``` | integer | Constructed BoolExpr evaluates to true when the left EF, right EF, or both, return true |
| ```BoolExpr.XNOR``` | integer | Constructed BoolExpr evaluates to true when either the left EF equals the right EF |
| ```BoolExpr.XOR``` | integer | Constructed BoolExpr evaluates to true when either the left EF or right EF returns true |
| ```BoolExpr.NAND``` | integer | Constructed BoolExpr evaluates to true when the left EF, right EF, or both, return false |
| ```BoolExpr.NOR``` | integer | Constructed BoolExpr evaluates to true when both the left and right EFs return false |
| ```BoolExpr.ALL``` | integer | Constructed BoolExpr evaluates to true when all the EFs return true |
| ```BoolExpr.ANY``` | integer | Constructed BoolExpr evaluates to true when at least one EF returns true |

<br/>

## Interface

This is the interface for functions passed to the constructors. Arguments are passed into the function upon evaluation.

```Lua
function ([self [, reverse [, ...]]))
```

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *self* | function \| table | The function currently being evaluated |
| *reverse* | boolean | ```true``` if the BoolExpr object the function belongs to was evaluated in reverse order |
| *...* | any | The arguments passed to the ```evaluate()``` call |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

For [BoolExpr Tables](99999_glossary.md/#definitions), the interface is below. It should be an array table.

```Lua
{expression_operator [, ...]}
```

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *expression_operator* | integer | The logical operator for evaluating expressions (Value must be one of the variables in the previous section) |
| *...* | function \| table | The expression(s) which *expression_operator* will evaluate |

<br/>

## Constructors

```Lua
function BoolExpr.New(expr)
```

Constructs a new BoolExpr object, which evaluates to true when *expr* returns true.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *expr* | function \| table | An EF, or another BoolExpr |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Not(expr)
```

Constructs a new BoolExpr object, which evaluates to true when *expr* returns false.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *expr* | function \| table | An EF, or another BoolExpr |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.And(left_expr, right_expr)
```

Constructs a new BoolExpr object, which evaluates to true when both *left_expr* and *right_expr* return true.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *left_expr* | function \| table | An EF, or another BoolExpr, serving as the left expression |
| *right_expr* | function \| table | An EF, or another BoolExpr, serving as the right expression |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Or(left_expr, right_expr)
```

Constructs a new BoolExpr object, which evaluates to true when *left_expr*, *right_expr*, or both, return true.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *left_expr* | function \| table | An EF, or another BoolExpr, serving as the left expression |
| *right_expr* | function \| table | An EF, or another BoolExpr, serving as the right expression |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Xnor(left_expr, right_expr)
```

Constructs a new BoolExpr object, which evaluates to true when both *left_expr* and *right_expr* are true or when both are false.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *left_expr* | function \| table | An EF, or another BoolExpr, serving as the left expression |
| *right_expr* | function \| table | An EF, or another BoolExpr, serving as the right expression |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Xor(left_expr, right_expr)
```

Constructs a new BoolExpr object, which evaluates to true when either *left_expr* or *right_expr* returns true.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *left_expr* | function \| table | An EF, or another BoolExpr, serving as the left expression |
| *right_expr* | function \| table | An EF, or another BoolExpr, serving as the right expression |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Nand(left_expr, right_expr)
```

Constructs a new BoolExpr object, which evaluates to true when *left_expr*, *right_expr*, or both, return false.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *left_expr* | function \| table | An EF, or another BoolExpr, serving as the left expression |
| *right_expr* | function \| table | An EF, or another BoolExpr, serving as the right expression |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Nor(left_expr, right_expr)
```

Constructs a new BoolExpr object, which evaluates to true when both *left_expr* and *right_expr* return false.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *left_expr* | function \| table | An EF, or another BoolExpr, serving as the left expression |
| *right_expr* | function \| table | An EF, or another BoolExpr, serving as the right expression |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.All(...)
```

Constructs a new BoolExpr object, which evaluates to true when all the EFs in ... return true.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *...* | function \| table | A list of EF, or BoolExprs, serving as expressions |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

```Lua
function BoolExpr.Any(...)
```

Constructs a new BoolExpr object, which evaluates to true when all the EFs in ... return true.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *...* | function \| table | A list of EF, or BoolExprs, serving as expressions |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | table | A newly constructed boolean expression |

<br/>

## Functions

```Lua
function BoolExpr:__call([reverse [, ...]])
```

Evaluates a BoolExpr

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *reverse* | boolean | If true, the boolean expression is evaluated in reversed order |
| *...* | any | Arguments passed into all the evaluated expressions |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | boolean | Boolean result of the evaluation |

<br/>

```Lua
function BoolExpr.evaluate(expr, [reverse [, ...]])
```

Similar to the function above, but can be used for manually constructed BoolExprs using ordinary table (see [Creating Boolean Expressions](2_creating-expressions.md/#manually-constructed-boolean-expressions) for a sample of manual construction using ordinary table)

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *expr* | function \| table | BoolExpr or BoolExpr table to be evaluated |
| *reverse* | boolean | If true, the expressions are evaluated in reversed order |
| *...* | any | Arguments passed into all the evaluated expressions |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | boolean | Boolean result of the evaluation |

<br/>

```Lua
function BoolExpr:compile()
```

Looks for cases in the underneath structure of the boolean expression that can be simplified. For example, a chained AND operator will be changed to an ALL operator and a chained OR will be converted to ANY. These are just examples and there are a lot more cases for simplification aside from these two.

This method does not direcly change the expression itself. Instead, the simplified expression is returned as a new BoolExpr object.

| Parameters: |||
|---|---|---|
| **Name** | **Type** | **Description** |
| *N/A* | *N/A* | *N/A* |

| Return value: |||
|---|---|---|
| **#** | **Type** | **Description** |
| *1* | BoolExpr | A new ```BoolExpr``` representing the simplified expression |

<br/>

Next: [Overview](1_overview.md)

[Back to top](#api-reference)
