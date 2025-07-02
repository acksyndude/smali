# Fixed Old Gradle Issue

## Build Commands
```
# Clean and build everything
./gradlew clean build

# Build without running tests (faster)
./gradlew clean build -x test

# Build specific modules
./gradlew :smali:build
./gradlew :baksmali:build
```

## Running the Tools
After building, you'll find the executable JARs in the build/libs directories:

### Smali (Assembler)
```
# Run smali assembler
java -jar smali/build/libs/smali-fat.jar [options] <input.smali> -o <output.dex>

# Example: assemble a smali file
java -jar smali/build/libs/smali-fat.jar HelloWorld.smali -o HelloWorld.dex
```

### Baksmali (Disassembler)
```
# Run baksmali disassembler
java -jar baksmali/build/libs/baksmali-fat.jar [options] <input.dex> -o <output_directory>

# Example: disassemble a dex file
java -jar baksmali/build/libs/baksmali-fat.jar app.dex -o disassembled/
```

### Quick Test
You can test the build with one of the example files:
```
# Build the project
./gradlew clean build

# Test with the HelloWorld example
java -jar smali/build/libs/smali-fat.jar examples/HelloWorld/HelloWorld.smali -o HelloWorld.dex
```


### About

smali/baksmali is an assembler/disassembler for the dex format used by dalvik, Android's Java VM implementation. The syntax is loosely based on Jasmin's/dedexer's syntax, and supports the full functionality of the dex format (annotations, debug info, line info, etc.)

Downloads are at  https://bitbucket.org/JesusFreke/smali/downloads/. If you are interested in submitting a patch, feel free to send me a pull request here.

See [the wiki](https://github.com/JesusFreke/smali/wiki) for more info/news/release notes/etc.

#### Support
- [github Issue tracker](https://github.com/JesusFreke/smali/issues) - For any bugs/issues/feature requests
- [#smali on freenode](http://webchat.freenode.net/?channels=smali) - Free free to drop by and ask a question. Don't expect an instant response, but if you hang around someone will respond.


#### Some useful links for getting started with smali

- [Official dex bytecode reference](https://source.android.com/devices/tech/dalvik/dalvik-bytecode.html)
- [Registers wiki page](https://github.com/JesusFreke/smali/wiki/Registers)
- [Types, Methods and Fields wiki page](https://github.com/JesusFreke/smali/wiki/TypesMethodsAndFields)
- [Official dex format reference](https://source.android.com/devices/tech/dalvik/dex-format.html)
