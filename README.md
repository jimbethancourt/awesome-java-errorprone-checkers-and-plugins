# awesome-java-errorprone-checkers-and-plugins
List of Errorprone Checkers and Plugins

The Fastest Way to Succeed is to Fail Faster
-----------------------------------------
[Google Errorprone](https://errorprone.info/) is a plugin for the Javac compiler that identifies code that may produce bugs and will fail the build, catching potentially buggy code as early as possible in the development cycle.  There are also additional checkers and Refaster libraries that others have written that can be used along with Errorprone.  This is a list of the Errorprone checkers and Refaster plugins that can be used with Errorprone to help make your code better.  

If you have identified new checkers that have clear usage instructions, please raise a Pull Request and I will happily approve it.

Errorprone Checkers
-------------------
Will fail the build if any potentially buggy code is identified
* [AutoDispose](https://github.com/uber/AutoDispose/) - Automatic binding+disposal of RxJava streams.
* [Configurable CheckReturnValue](https://github.com/ZacSweers/configurable-checkreturnvalue/)
* [Error Prone SLF4J](https://github.com/KengoTODA/errorprone-slf4j) - An Error Prone plugin for SLF4J
* [GRPC Java API Checker](https://github.com/grpc/grpc-java-api-checker) - An Error Prone plugin that checks for usages of grpc-java experimental or internal APIs.
* [Guava Cleanser](https://github.com/sisidra/guava-cleanser) - Fail the build on Guava usage
* [Hyperledger Errorprone Checks](https://github.com/hyperledger/besu/tree/master/errorprone-checks)
* [Nope'n Checker](https://github.com/JakeWharton/nopen/) - An error-prone checker which requires that classes be final, abstract or annotated with @Open.
* [NullAway](https://github.com/uber/NullAway/) - A tool to help eliminate NullPointerExceptions (NPEs) in your Java code with low build-time overhead
* [Piranha](https://github.com/uber/piranha/blob/master/java/README.md) - A tool for refactoring code related to feature flag APIs
* [Rx-Error-Prone](https://github.com/bangarharshit/Rx-error-prone) - Error prone checks for RxJava


Refaster Extensions
-------------------
Will modify the codebase to remove potentially buggy code as part of the build
* [AssertJ Automation](https://github.com/palantir/assertj-automation) - Automatic code rewriting for AssertJ using error-prone and refaster
* [Baseline Refaster Testing](https://github.com/palantir/gradle-baseline) - A set of Gradle plugins that configure default code quality tools for developers.
* [Digitalascent ErrorProne Flogger](https://github.com/cslee00/digitalascent-errorprone-logger) - Error prone checks & refactorings supporting Google Flogger

**Methodology:**
Usages of the following dependencies that have valid Github repositories were identified and listed above.
* [error_prone_check_api](https://mvnrepository.com/artifact/com.google.errorprone/error_prone_check_api/usages)
* [error_prone_core](https://mvnrepository.com/artifact/com.google.errorprone/error_prone_core/usages)
* [error_prone_test_helpers](https://mvnrepository.com/artifact/com.google.errorprone/error_prone_test_helpers/usages) 
* [error_prone_refaster](https://mvnrepository.com/artifact/com.google.errorprone/error_prone_refaster/usages)



Lombok + Errorprone use Public Service Announcement
----------------------------------
If you are using both Errorprone and Lombok in your project, you will need to specify the Lombok annotation processor path in the compiler plugin.
For Maven, the following configuration will need to be used for the **maven-compiler-plugin**
For example:
```xml
        <plugins>
          ...
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>${maven-compiler-plugin.version}</version>
                <configuration>
                    <source>${mvn.compiler.source}</source>
                    <target>${mvn.compiler.target}</target>
                    <compilerArgs>
                        <arg>-XDcompilePolicy=simple</arg>
                        <arg>-Xplugin:ErrorProne</arg>
                    </compilerArgs>
                    <annotationProcessorPaths>
                        <path>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                            <version>${lombok.version}</version>
                        </path>
                        <path>
                            <groupId>com.google.errorprone</groupId>
                            <artifactId>error_prone_core</artifactId>
                            <version>${errorprone.version}</version>
                        </path>
                    </annotationProcessorPaths>
                </configuration>
            </plugin>
          ...
        </plugins>               

```
