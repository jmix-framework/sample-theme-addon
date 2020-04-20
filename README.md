# sample-theme-addon

An example of a theme add-on that can be added to a Jmix project as a dependency.

## Theme add-on

Theme add-ons may provide SCSS files for a theme compilation. They must comply with the following requirements:

* The `VAADIN/addons/<addon-name>` directory must be created in a JAR-file
* The `VAADIN/addons/<addon-name>` directory must contain `<addon-name>.scss` file
* The `<addon-name>.scss` file must contain definition of `@mixin <addon-name>`

```
// mandatory mixin definition
@mixin <addon-name> {
  .v-button.demo-button {
    background-color: red;
  }
}
```

* The JAR-file must contain the `Vaadin-Stylesheets` key in the Manifest:

```
jar.manifest {
    attributes(['Vaadin-Stylesheets': 'VAADIN/addons/<addon-name>/<addon-name>.scss'])
}
```

## Adding an add-on to a project

* Build and install add-on to a maven local:

```
./gradlew clean assemble install
```

* Include add-on dependency to a project:

```
implementation 'com.example:sample-theme-addon:1.0-SNAPSHOT'
```
