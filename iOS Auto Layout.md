iOS Auto Layout
=========

* Constraint-based descriptive layout system.  What's that mean?
    * For example: Centered horizontally in its superview
    * Fixed distance from the bottom, as linear equations!
    * System calculates layout automatically.
    
So, how do we auto-layout?
-----

Checkbox in the utilities inspector (Document) to "Enable auto-layout".  Note that the snap guidelines in auto-layout have a different meaning than before.  For example, center-aligning and 10 pixels from the bottom will always hold that ratio, regardless of orientation!

* Constraints are full-fledged outlets in IB; you can configure them in code!  If in code, you have to create the constraints, and then add them to the view.

* Lives within NSLayoutConstraint.h (don't have to import, already included in UIKit for you)

The general equation is as the following: 

```item1.attribute1 = multiplier * item2.attribute2 + constant (equals sign can also be inequality)```

```+ (id)constraintWithItem: attribute: relatedBy: toItem: attribute: multiplier: constant:```

For example...

In general, Button.centerX = Superview.centerX and Button.bottom = Superview.bottom - <padding> for the example in the keynote.

To add the constraint...

```- (void)addConstraint:(NSLayoutConstraint *)constraint```

Constraints
-----

* Can apply to any 2 views, regardless of heirarchy!
* Maximum & minimums w/ inequalities
* Can be prioritized!  Required priority level is 1000, can set priority anytime before constraint is added to view
* Use the attributes inspector on a particular constraint to set the priority

Inequality Constraints!
-----

* Editor > Pin > "Pin Leading Space to the Superview"
* You can then change it to be **great than or equal to** it's superview

Cross-View Hierarchy Constraints
-----

Often have a container view containing a particular portion of the UI.  You may end up removing a constraint on a particular object that is defined in IB in code, to allow you to define your own constraints.  Note: Don't do cross-window constraints! :)


Phases of Display
-----

With defined constraints, you may need to "poke" the system and inform it that it needs to update the display.  For example, maybe a subview (such as a badge) is added to the view, and things need to be rearranged proportionally.  The three steps that take place, in order, are the following:

* Update Constraints - bottom up with ```-setNeedsUpdateConstraints```

* Layout - top down with ```-setNeedsLayout```

* Display - top down with ```-setNeedsDisplay```

**But what about constraining a button size, for example?  What if you want a button to be a particular size?**

```intrinsicContentSize``` - returns actual sizes of views, can get information about the element of interest


Things That Can Go Wrong
-----

*Interface Builder is trying to help prevent you from things going wrong when laying out your view.  Typically, you will see weirdness when defining constraints/layouts in code.  Woudln't it be nice to define these as a picture in code?  Check this out:*

Representing Your Layouts in Code (aka Awesome)
----

```[NSLayoutConstraint constraintsWithVisualFormat: @"[cancelButton]-[acceptButton]" options:0 metrics:nil views:viewsDictionary];```

Use ```NSDictionaryOfVariableBindings``` if views are defined as properties.  Awesome.

What if you want to define specific sizes of the buttons?

```[NSLayoutConstraint constraintsWithVisualFormat: @"[cancelButton(50)]-[acceptButton(50)]" options:0 metrics:nil views:viewsDictionary];```

Use ```_autolayoutTrace``` in the debugger to see the defined layouts for your view hierarchy.


Compatibility
-----

I'm ready to conver to auto-layout, but how do I begin?  You can configure to use auto-layout in all, or just certain parts of your application.

Use ```translatesAutoresizingMaskIntoConstraints``` == NO to make your constrained views not conflict with non-constrained views.  IB will handle this for you, so this would only be for using in code.