## Enable java-operator-plugins for operator-sdk

To use java-operator-plugins for java operators we need to clone the operator-sdk repo.

### Updates in Operator-SDK go.mod

- Add the kubebuilder plugin to `go.mod`

```
github.com/operator-framework/java-operator-plugins v0.0.0-20210225171707-e42ea87455e3
```

- Replace the java-operator-plugins path in go-mod pointing to the local dir of your kube-builder repo. Example.

```
github.com/operator-framework/java-operator-plugins => /Users/sushah/go/src/github.com/sujil02/java-operator-plugins
```

### Build and Install the Operator-SDK
```
go mod tidy
make install
```

Now that the plugin is integrated with the `operator-sdk` you can run the `init` command to generate the sample java operator

- Use the quarkus plugin flag
- Pick the domain and project name as prefered.

```
operator-sdk init --plugins quarkus --domain xyz.com --project-name java-op
```

Once the operator is scaffolded check for the following files

```
├── PROJECT
├── pom.xml
└── src
    └── main
        ├── java
        │   └── com
        │       └── xyz
        │           └── JavaOpOperator.java
        └── resources
            └── application.properties

```
