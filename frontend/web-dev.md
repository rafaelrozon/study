---
description: General Web Development Topics
---

# Miscellaneous Web Dev

## Dev Lessons

* Don’t import anything outside the src folder, because if static files are imported then when it’s build, the relative paths to those files may be broken if the dist folder doesn’t have the same structure as the src.
* Avoid deeply nested folders in the distribution folder of rpm packages: dist/… is better then dis/src/...
* Make sure to not export files that are not important when publishing packages to npm. Use npm ignore file for that



