iOS Auto Layout
=========


* Constraint-based descriptive layout system.  What's that mean?
    * For example: Centered horizontally in its superview
    * Fixed distance from the bottom, as linear equations!
    * System calculates layout automatically.
    
How do we do auto-layout?
-----

Checkbox in the utilities inspector (Document) to "Enable auto-layout".  Note that the snap guidelines in auto-layout have a different meaning than before.  For example, center-aligning and 10 pixels from the bottom will always hold that ratio, regardless of orientation!

* Constraints are full-fledged outlets in IB; you can configure them in code!  If in code, you have to create the constraints, and then add them to the view.

* Lives within UILayoutConstraint.h (don't have to import, already included in UIKit for you)

The general equation is as the following: 

```item1.attribute1 = multiplier * item2.attribute2 + constant (equals sign can also be inequality)```

```+ (id)constraintWithItem: attribute: relatedBy: toItem: attribute: multiplier: constant:```

For example...

In general, Button.centerX = Superview.centerX and Button.bottom = Superview.bottom - <padding> for the example in the keynote.

To add the constraint...

```- (void)addConstraint:(UILayoutConstraint *)constraint```

**But which view do we add the constraint to?**


