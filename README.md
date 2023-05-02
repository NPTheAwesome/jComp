# jComp

A simple and easy to use bash script to simplify creating of java projects.
Currently on Alpha version number 0.2.3

## Installation and Dependencies

The application depends on the following packages.

* JDK (obviously)
* grep
* sed
* GIT (optional, but suggested)

To install the script on a linux system, clone the repository and run the install.sh script. 

```
./install
```

By default the install script will attempt to put the jcomp script in /usr/bin, if however you would like to install jcomp at a different location pass the desire directory to the install script.

```
./install /bin
```

Remember to install as root if needed.

## Use and Flags

### Creating a Project

In order to make a new project, navigate to the directry you would like to plaace your project in, and run jcomp using the -g flag passing the name of your project. If a sub directory with the name you passed does not exist it will be created. A brand new project will built up inside of the new project directory. For example:

```
jcomp -g ProjectName
```

### Compiling a Project

To simply compile a project to a binary run the jcomp command without any flags or parameters. This will create a jar file in the bin/ directory, and create a shell script in the root of the project directory to run it.

```
jcomp
```

If you want jcomp to clean up after itself and delete the class files after compiling run jcomp with the -c flag.

```
jcomp -c
```

### Running and Testing

If you want to run the program immediately after compiling run jcomp with the -r flag.

```
jcomp -r
```

If you want just to test a change, and have jcomp delete the class files, and the jar file after running once, run jcomp with the -t flag.

```
jcomp -t
```

### Overwriting Configuration

If you want to use jcomp and overwrite a specific parameter from the config file without modifying the file itself, there are several flags that can be used to overwrite specfic flags.

If you want to change the name of the binary that is produced use the -o flag.

```
jcomp -o ApplicationName
```

If you want to change the name of the file to use as the entry point use the -e flag. The parameter should be in the format of `package.file` with no .java file extension.

```
jcomp -e package.file
```

If you want to change the creator credited in the manifest file, use the -b flag.

```
jcomp -b "Firstname Lastname"
```

If you want to change which manifest to load from the configuration directory, use the -m flag.

```
jcomp -m ManfiestName
```

If you want to change which config file to load from the configuration directory, use the -s flag.

```
jcomp -s ConfigName
```

if you want to change the directory to load configuration files from, use the -i flag.

```
jcomp -i ./Configuration/Directory
```

### Help and Debugging

If you want to see a print out of all of the flags that you can use with jcomp, use the -h flag.

```
jcomp -h
```

If you want to see a verbose log of all of the things jcomp is doing, use the -v flag.

```
jcomp -v
```

You can use most of the flags with other flags. Exceptions include the -g flag which ignores all other flags, the -m flag which ignores the -b and -e flags, -h which ignores all flags other than -v, and -t which ignores -r and -c.

## Structure of a Project

Each project will contain four directories by default, source/, classes/, bin/ and etc/.

* source/ will be the location of your primary source code package, and will have a hello world program, Main.java, inside of a new project.
* classes/ will be the location of your .class binaries associated with your source files.
* bin/ will be the location of your output binaries after compilation.
* etc/ will be the location of your configuration files, and will contain a config file and a manifest file inside of a new project.

## Configuration and Defaults

Each project has a config file located at etc/config which controls several important parameters for jcomp. The parameters and their default values are as follows:

* executable_directory; the directory that the jar binaries are place in, by default this is "./bin/"
* source_directories_string; the comma seperated list of directories to load source code from, by default this is "./source/"
* classes_directory; the directory that the class binaries are placed in, by default this is "./classes"
* manifest_name; the name of the manifest file to be loaded from the config directory, by default this is "auto_manifest"
* entry_name; the name of the source file to use as an entry point for the program, in the format of `package.File`, by default this is "source.Main"
* creator_name; the name of the project's creator to be credited in the manifest file, by default this is "jComp"
* executable_name; the name of the application to be compiled to, by default this is the name of the project with .jar following, so if your project was called "white_elephant" the executable name would be "white_elphant.jar" by default.
* launch_prefix; the prefix added to the executable name for the launch script created when compiling, by default this is "app_". if your project was called "white_elephant" the name of the launch script would be "app_white_elephant.sh" by default.

Documentation last modified May 2nd 2023.
