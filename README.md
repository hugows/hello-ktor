This now works. Compile with "gradle build" and run with something like:

`java -jar build/libs/ktor-hello-1.0-SNAPSHOT.jar`

I had to add this to the build.gradle so that kotlin runtime was added to the jar:

```
jar {
    manifest {
        attributes 'Main-Class': 'foo.bar.MainKt'
    }
    from {
       configurations.compile.collect { it.isDirectory() ? it : zipTree(it) 
       }
    }
}
```
