# java-notes
java notes moved from OneNote

## Maven notes  

### Creating jar with dependencies  

There is more than one way to do it. Simplest one is below.  

```
 <build>
            <plugins>
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-assembly-plugin</artifactId>
                    <executions>
                        <execution>
                            <phase>package</phase>
                            <goals>
                                <goal>single</goal>
                            </goals>
                            <configuration>
                                <archive>
                                    <manifest>
                                        <mainClass>
                                            org.myapp.MainClass
                                        </mainClass>
                                    </manifest>
                                </archive>
                                <descriptorRefs>
                                    <descriptorRef>jar-with-dependencies</descriptorRef>
                                </descriptorRefs>
                            </configuration>
                        </execution>
                    </executions>
                </plugin>
            </plugins>
    </build>
```  

## Switching java versions in RedHat  

There is a short and concise article written for exactly this purpose [How to install Java 8 and 11 on Red Hat Enterprise Linux 8](https://developers.redhat.com/blog/2018/12/10/install-java-rhel8/)  

### Switch java and javac to Java 1.8  

```
java8=$(alternatives --display java|grep "family java-1.8"|awk '{print $1}')
alternatives --set java $java8
java -version

javac8=$(alternatives --display javac|grep "family java-1.8"|awk '{print $1}')
alternatives --set javac $javac8
javac -version
```  

### Switch java and javac to Java 11

```
java11=$(alternatives --display java|grep "family java-11"|awk '{print $1}')
alternatives --set java $java11
java -version

javac11=$(alternatives --display javac|grep "family java-11"|awk '{print $1}')
alternatives --set javac $javac11
javac -version
```
