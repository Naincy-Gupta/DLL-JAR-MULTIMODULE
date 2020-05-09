# epson-receipt-printer-jars

This project includes the EPSON Receipt Printer JPOS drivers and Dll's needs to be imported at Peripheral Server to interact with EPSON Receipt Printer 

<b>Usage</b>

To import all the jars using parent pom, add a type tag `<type>pom</type>` while adding its dependency in your project.

Usage
```xml
<dependency>
    <groupId>eai3530951.com.fedex.peripherals.epson</groupId>
    <artifactId>epsonlibs</artifactId>
    <version>0.0.1</version>
    <type>pom</type>
</dependency>
```

To unpack all the DLLs at a desired location, use `maven-dependency-plugin`.

Usage
```xml
...
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-dependency-plugin</artifactId>
	<version>3.1.1</version>
	<executions>
		<execution>
	    	<id>unpack</id>
			<phase>package</phase>
			<goals>
				<goal>unpack</goal>
			</goals>
			<configuration>
				<artifactItems>
					<artifactItem>
						<groupId>eai3530951.com.fedex.peripherals.epson</groupId>
						<artifactId>compressed-dlls-epson</artifactId>
						<version>0.0.1.RELEASE</version>
						<type>zip</type>
						<overWrite>true</overWrite>
						<outputDirectory>${project.build.directory}/alternateLocation</outputDirectory>
					</artifactItem>
				</artifactItems>
			</configuration>
		</execution>
	</executions>
</plugin>
...
```
Set the path in `<outputDirectory>${project.build.directory}/alternateLocation</outputDirectory>` accordingly.