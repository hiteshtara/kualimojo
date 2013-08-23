
The following example walk s you through how to create your plug in for the pom these plug ins are handy when you want to do certain task associated with your project 


compile	Compiles the Java code for the plugin and builds the plugin descriptor
test	Runs the plugin's unit tests
package	Builds the plugin jar
install	Installs the plugin jar in the local repository
deploy	Deploys the plugin jar to the remote repository
For example, to run the simple mojo in the sample plugin, you would enter "mvn sample.plugin:hello-maven-plugin:1.0-SNAPSHOT:sayhi" on the command line.
Make sure thuiis defined in the build phase of project like
 <build>
    <plugins>
      <plugin>
        <groupId>sample.plugin</groupId>
        <artifactId>hello-maven-plugin</artifactId>
        <version>1.0-SNAPSHOT</version>
      </plugin>
    </plugins>
  </build>
  Attaching the Mojo to the Build Lifecycle

You can also configure your plugin to attach specific goals to a particular phase of the build lifecycle. Here is an example:
 <build>
    <plugins>
      <plugin>
        <groupId>sample.plugin</groupId>
        <artifactId>hello-maven-plugin</artifactId>
        <version>1.0-SNAPSHOT</version>
        <executions>
          <execution>
            <phase>compile</phase>
            <goals>
              <goal>sayhi</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  Parameters

It is unlikely that a mojo will be very useful without parameters. Parameters provide a few very important functions:

It provides hooks to allow the user to adjust the operation of the plugin to suit their needs.
It provides a means to easily extract the value of elements from the POM without the need to navigate the objects.