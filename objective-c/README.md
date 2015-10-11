# References

- [Ry’s Objective-C Tutorial](http://rypress.com/tutorials/objective-c/index) **[MUST READ]** :bangbang:
- *Effective Objective-C 2.0* **[MUST READ]** :bangbang:
- http://nshipster.com/

# Xcode

- Install these plugins with [Alcatraz](http://alcatraz.io/): GitDiff, VVDocumenter-Xcode, ClangFormat, read more at http://nshipster.com/xcode-plugins/
- Edit -> CLang Fromat -> File, Edit -> CLang Fromat -> Enable Format on Save

# Style Guide

- https://github.com/NYTimes/objective-c-style-guide
- https://github.com/github/objective-c-style-guide
- Delete Xcode generated header comment, because they're useless and very likely to be outdated

# Grammar

- [@property](http://rypress.com/tutorials/objective-c/properties)
- [Don't use accessor methods in init and dealloc methods](http://stackoverflow.com/questions/3424382/why-shoudnt-i-use-accessor-methods-in-init-methods)
- Instance variables declared in the implementation are implicitly hidden (effectively private) and the visibility cannot be changed - @public, @protected and @private do not produce compiler errors (with the current Clang at least) but are ignored.
- [ivars, properties and extension](http://stackoverflow.com/questions/12632285/declaration-definition-of-variables-locations-in-objectivec/12632467#12632467)
- [Use weak self to break retain circle](http://stackoverflow.com/questions/20030873/always-pass-weak-reference-of-self-into-block-in-arc)
