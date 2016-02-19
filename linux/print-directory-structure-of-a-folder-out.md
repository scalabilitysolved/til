# Print directory structure of a folder out

Tree is a handy little linux tool that'll allow you to print out the directory structure of any folder, it's not bundled as a default so first you'll need to install it:

```bash
sudo apt-get install tree
```

Then you can run it like so:

* Only show folder structure

```bash
tree -d
```

and produces:

```bash
├── main
│   ├── java
│   │   └── com
│   │       └── scalesolved
│   │           ├── client
│   │           ├── commands
│   │           ├── configuration
│   │           │   └── mapping
│   │           ├── controllers
│   │           ├── entities
│   │           ├── models
│   │           └── repositories
│   └── resources
│       ├── static
│       └── templates
└── test
    └── java
        └── com
            └── scalesolved
                └── client
```

* Show folders and files

```bash
tree
```

and produces:

```bash
├── main
│   ├── java
│   │   └── com
│   │       └── scalesolved
│   │           ├── client
│   │           │   ├── SlackClient.java
│   │           │   ├── SlackMessage.java
│   │           │   └── SlackResponse.java
│   │           ├── commands
│   │           │   ├── IncomingSlashCommand.java
│   │           │   └── OutGoingSlashCommand.java
│   │           ├── configuration
│   │           │   ├── JacksonConfiguration.java
│   │           │   └── mapping
│   │           │       ├── Mapper.java
│   │           │       ├── MappingConfiguration.java
│   │           │       └── OrikaMapperAdapter.java
│   │           ├── controllers
│   │           │   └── StatusController.java
│   │           ├── entities
│   │           │   ├── Status.java
│   │           │   ├── User.java
│   │           │   └── ZonedDateTimeConverter.java
│   │           ├── models
│   │           ├── repositories
│   │           │   ├── StatusRepository.java
│   │           │   └── UserRepository.java
│   │           ├── RequestFilter.java
│   │           └── UpfetchApplication.java
│   └── resources
│       ├── application.properties
│       ├── logback.xml
│       ├── static
│       └── templates
└── test
    └── java
        └── com
            └── scalesolved
                ├── client
                │   └── SlackClientTest.java
                └── UpfetchApplicationTests.java
```

* Limit recursion through the directory to X steps

```bash
tree -L 3
```

and produces:

```bash
├── main
│   ├── java
│   │   └── com
│   └── resources
│       ├── application.properties
│       ├── logback.xml
│       ├── static
│       └── templates
└── test
    └── java
        └── com
```

* If you have a ton of folders and need to find a specific one and how it routes back to the parent directory then you can do:

```bash
tree -d | grep -B100 mapping

```

and produces:

```bash
├── main
│   ├── java
│   │   └── com
│   │       └── scalesolved
│   │           ├── client
│   │           ├── commands
│   │           ├── configuration
│   │           │   └── mapping
```




