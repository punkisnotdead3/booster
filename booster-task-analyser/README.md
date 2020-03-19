# booster-task-analyser

This module is used for static analysing.

## Getting Started

Start analysing by executing the following command

```bash
./gradlew analyseDebug
```

or 

```bash
./gradlew analyseRelease
```

or

```bash
./gradlew analyse
```

## Analyser Reports

The [dot](https://www.graphviz.org/doc/info/lang.html) format reports is located at `build/reports/${variant}/booster-task-analyser/`,  you can convert the dot files to PNGs by using the following command:

```bash
find build/reports -name '*.dot' | xargs -t -I{} dot -O -Tpng {}
```

Here is an example generated by dot:

![com.didiglobal.booster.demo.MainActivity](../assets/com.didiglobal.booster.demo.MainActivity.dot.png)

## Properties

The following table shows the properties that transformer supports:

| Property                         | Description                                                                                   | Example                             |
| -------------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------- |
| `booster.task.analyser.blacklist` | URI of API black list（Using [built-in API list](src/main/resources/blacklist.txt) by default）| file:///Users/booster/blacklist.txt |
| `booster.task.analyser.whitelist` | URI of API white list（Using [built-in API list](src/main/resources/whitelist.txt) by default）| file:///Users/booster/whitelist.txt |

The properties can be passthrough the command line as following:

```bash
./gradlew assembleDebug -Pbooster.task.analyser.whitelist=file:///Users/booster/whitelist.txt
```

or configured in the `gradle.properties`:

```properties
booster.task.analyser.whitelist=file:///Users/booster/whitelist.txt
```