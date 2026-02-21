# Gradle Build Fat jar

```
tasks.register('createFatJar', Jar) {

    String appName = "HelloWorld"
    String mainClass = "com.example.HelloWorld"

    manifest {
        attributes 'Implementation-Title': appName,
                'Implementation-Version': version,
                'Main-Class': mainClass
    }

    archiveBaseName = appName + "-all"
    duplicatesStrategy = DuplicatesStrategy.EXCLUDE

    exclude "META-INF/*.SF"
    exclude "META-INF/*.DSA"
    exclude "META-INF/*.RSA"

    from { configurations.runtimeClasspath.collect { it.isDirectory() ? it : zipTree(it) } }

    // Include project sources (src/main/java, src/main/resources, etc.) into the jar
    from(sourceSets.main.allSource) {
        into("src")
    }

    // Include README in the jar (kept at jar root)
    from("readme.md")

    // Also copy Gradle build scripts into the src folder inside the jar
    from("build.gradle") {
        into("src")
    }
    from("settings.gradle") {
        into("src")
    }

    with jar
}
```

## Run

```
tasks.register('executeApp', JavaExec) {
    mainClass = "com.example.HelloWorld"
    classpath = sourceSets.main.runtimeClasspath
}
```
