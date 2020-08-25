# Web Dev

1. Don’t import anything outside the src folder, because if static files are imported then when it’s build, the relative paths to those file may be broken if the dist folder doesn’t have the same structure as the src.
2. Avoid deep nested folders in the distribution folder of rpm packages: dist/… is better then dis/src/...
3. Make sure to not export files that are not important when publishing packages to npm. Use npm ignore file for that
4. 
