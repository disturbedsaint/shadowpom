# shadowpom
Demonstrates error in pom files when building shadow jars.

# How to reproduce

1. `./gradlew :SomeLib2:publishToMavenLocal`
2. `./gradlew :SomeLib1:publishToMavenLocal`
3. `./gradlew :SomeApp:run`
4. Inspect SomeLib1's pom file by running `cat ~/.m2/repository/shadowpom/SomeLib1/1.0/SomeLib1-1.0.pom`
   * Notice that it is not referencing the `all` classifier.
5. Change `SomeLib1/build.gradle` to refer to the published version of SomeLib2 and re-run steps 2 - 4.
   * Notice that the pom file does reference the `all` classifier.
