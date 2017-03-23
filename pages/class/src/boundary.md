---
layout: class
title: Boundary
namespace: Freesewing
tags: [class documentation]
permalink: /class/boundary
---
## Description 

The [`Boundary`](boundary) class holds boundary information that can apply to a path or an entire part.

> Boundary means the smalles possible bounding box that contains all paths. 
> See [`BezierToolbox::bezierBoundary`](beziertoolbox#bezierboundary) for an example.

Note that [`Boundary`](boundary) is only used to store this information. It does not calculate
the bounding box itself.

## Typical use

The [`Boundary`](boundary) class is internal. It is used to hold boundary information for 
[`Part`](part) and [`Path`](path) objects.

## Public methods

### setTopLeft

```php?start_inline=1
void setTopLeft( 
    \Freesewing\Point $point 
)
```
Assigns the [`Point`](point) `$point` to the `topLeft` property.

### setBottomRight

```php?start_inline=1
void setBottomRight( 
    \Freesewing\Point $point 
)
```
Assigns the [`Point`](point) `$point` to the `bottomRight` property.

### getTopLeft

```php?start_inline=1
\Freesewing\Point getTopLeft() 
```
Returns the [`Point`](point) stored in the `topLeft` property, if any.

### getBottomRight

```php?start_inline=1
\Freesewing\Point getBottomRight() 
```
Returns the [`Point`](point) stored in the `bottomRight` property, if any.

## See also
{% include classFooter.html %}
* TOC - Do not remove this line
{:toc}
