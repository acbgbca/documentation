# Maven

## Skip Tests

Run with ```-DskipTests```

## Run Single Test

Run with ```-Dtest=ClassName```

Note: You only need the class name, not the full class with package. To run a single test within a class use ```-Dtest=ClassName#method```

## Build a specific module

Run with ```-pl <module>```, where &lt;module&gt; is the name of the module to build

If that module has dependencies, include ```-am``` in the command to build related modules. I.e. ```-pl <module> -am```
