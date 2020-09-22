For the build to work:
- Uncomment `implementation project(":lib")`and comment `implementation "com.acme:lib:0.0.1-SNAPSHOT"` out
- run `./gradlew build`

Fro the build to break
- Uncomment `implementation "com.acme:lib:0.0.1-SNAPSHOT"`and comment `implementation project(":lib")` out
- Install the lib using `./gradlew :lib:install`
- run `./gradlew build`

You will get a message similar to 
```
Could not determine the dependencies of task ':app:shadowJar'.
> Could not resolve all dependencies for configuration ':app:runtimeClasspath'.
   > Could not resolve io.micronaut:micronaut-bom:2.0.0.
     Required by:
         project :app > com.acme:lib:0.0.1-SNAPSHOT
      > No matching variant of io.micronaut:micronaut-bom:2.0.2 was found. The consumer was configured to find a runtime of a library compatible with Java 11, packaged as a jar, and its dependencies declared externally but:
          - Variant 'apiElements' capability io.micronaut:micronaut-bom:2.0.2:
              - Incompatible because this component declares an API of a platform and the consumer needed a runtime of a library
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about its target Java version (required compatibility with Java 11)
                  - Doesn't say anything about its elements (required them packaged as a jar)
          - Variant 'enforcedApiElements' capability io.micronaut:micronaut-bom-derived-enforced-platform:2.0.2:
              - Incompatible because this component declares an API of an enforced platform and the consumer needed a runtime of a library
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about its target Java version (required compatibility with Java 11)
                  - Doesn't say anything about its elements (required them packaged as a jar)
          - Variant 'enforcedRuntimeElements' capability io.micronaut:micronaut-bom-derived-enforced-platform:2.0.2 declares a runtime of a component:
              - Incompatible because this component declares an enforced platform and the consumer needed a library
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about its target Java version (required compatibility with Java 11)
                  - Doesn't say anything about its elements (required them packaged as a jar)
          - Variant 'runtimeElements' capability io.micronaut:micronaut-bom:2.0.2 declares a runtime of a component:
              - Incompatible because this component declares a platform and the consumer needed a library
              - Other compatible attributes:
                  - Doesn't say anything about how its dependencies are found (required its dependencies declared externally)
                  - Doesn't say anything about its target Java version (required compatibility with Java 11)
                  - Doesn't say anything about its elements (required them packaged as a jar)
```