thrift-maven-plugin
===================

This project was originally forked from the thrift repo so that I could release
a version of the plugin with this
[fix](https://issues.apache.org/jira/browse/THRIFT-3419).

However, it seems this plugin is pretty short on documentation now (had some in
a previous incarnation). So here's some!

Getting Started
---------------

First up, configure your plugin like so:


            <plugin>
                <groupId>org.apache.thrift</groupId>
                <artifactId>thrift-maven-plugin</artifactId>
                <version>0.9.3-ddc_0.0.1</version>
                <executions>
                    <execution>
                        <id>thrift-sources</id>
                        <phase>generate-sources</phase>
                        <goals>
                            <goal>compile</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>thrift-test-sources</id>
                        <phase>generate-test-sources</phase>
                        <goals>
                            <goal>testCompile</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>

Then, add the runtime dependencies thrift requires. I usually exclude the http
dependencies unless I actually need them.

        <dependency>
            <groupId>org.apache.thrift</groupId>
            <artifactId>libthrift</artifactId>
            <version>0.9.3</version>
            <exclusions>
                <exclusion>
                    <groupId>org.apache.httpcomponents</groupId>
                    <artifactId>httpclient</artifactId>
                </exclusion>
                <exclusion>
                    <groupId>org.apache.httpcomponents</groupId>
                    <artifactId>httpcore</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

That's it! `mvn clean install` and you should have some shiny new generated
classes under `target/generated-sources/thrift/`.

Configuration Options
---------------------

TODO: ...

Exporting thrift definitions to a maven repo
--------------------------------------------

TODO: basic standalone example
TODO: include maven dependencies for included thrift files in pom that is deployed

Importing thrift definitions from a maven repo
----------------------------------------------

TODO: example of generating classes for a specific thrift file (excluding others on the classpath)
TODO: example of generating classes for a local thrift file that depends on others on the classpath

