# schema-parent-pom

This a parent pom for schema projects.

 This parent pom implements the following:

  * Compose data models using maven dependency framework. Use the maven to re-use, version, release and publish avro data models. (test-schema -> test-schema-common)

  * Validate avro schemas ([extensile](http://www.spf4j.org/spf4j-avro-components/maven-avro-schema-plugin/avro-validate-mojo.html)). (documentation, naming,  compatibility with previously released versions...)

  * Add a unique ID to the schemas (mvnId = "group:artifact:version:id")

  * Generate and publish java classes along with javadoc. (publishing for other languages can se set up) (@Imutable support, @Nullable/@Nonnull) [see](https://bintray.com/zolyfarkas/core/download_file?file_path=org%2Fspf4j%2Favro%2Fexamples%2Ftest-schema%2F1.1%2Ftest-schema-1.1.jar)

  * Generate package and publish the avro schemas, [see](https://bintray.com/zolyfarkas/core/download_file?file_path=org%2Fspf4j%2Favro%2Fexamples%2Ftest-schema%2F1.1%2Ftest-schema-1.1-avsc.jar).
  
  * Generate and publish avrodoc, [see](https://bintray.com/zolyfarkas/core/download_file?file_path=org%2Fspf4j%2Favro%2Fexamples%2Ftest-schema%2F1.1%2Ftest-schema-1.1-avrodoc.jar) for  maven repo publish
    [or](https://zolyfarkas.github.io/fred-schema/) for gh-pages doc publish.


Here is how a schema project that uses this parent will look like:

    <?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"       xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
      <groupId>org.spf4j.avro.examples</groupId>
      <artifactId>test-schema</artifactId>
      <packaging>jar</packaging>
      <version>MY_VERSION</version>
      <name>${project.artifactId}-${project.version}</name>
      <description>Avro schema example</description>
      <parent>
        <groupId>org.spf4j.avro</groupId>
        <artifactId>schema-parent-pom</artifactId>
        <version>LATEST</version>
      </parent>
      <dependencies>
        <dependency> <!-- this schema will re-use schema's from this dependency -->
            <groupId>org.spf4j.avro.examples</groupId>
            <artifactId>test-schema-common</artifactId>
            <version>1.5</version>
        </dependency>
      </dependencies>
    </project>

for an example please see [core-schema](https://github.com/zolyfarkas/core-schema)
