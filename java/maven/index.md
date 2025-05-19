# Maven

## Skip Tests

Run with ```-DskipTests```

## Run Single Test

Run with ```-Dtest=ClassName```

Note: You only need the class name, not the full class with package. To run a single test within a class use ```-Dtest=ClassName#method```

## Run a Test in debug mode

Run with ```mvn -Dmaven.surefire.debug test```

The run will pause until you connect the debugger on port 5005, and then the tests to execute. Useful if your IDE is playing up and won't run the tests.

## Build a specific module

Run with ```-pl <module>```, where &lt;module&gt; is the name of the module to build

If that module has dependencies, include ```-am``` in the command to build related modules. I.e. ```-pl <module> -am```

## Don't stop on failed module

When building and testing a multi-module maven project, when one module fails the build stops. To continue testing the rest of the modules, use ```--fail-at-end``` or ```-fae```

E.g.
```
mvn clean test --fail-at-end
```

Note: If a module fails, it will continue building and testing the other modules, however anything that depends on that module will also be skipped. To force all modules to be tested regardless, use ```--fail-never``` or ```-fn```

## Multi-Threaded builds

To run builds using multiple threads use ```-T```.

I.e.

Two threads: ```mvn -T 2 clean test```
One thread per core: ```mvn -T 1C clean test```

Depending on the computer and the structure of your project, this can have a significant performance impact:
Standard: 08:56 min
One thread per core (8 cores): 05:32 min