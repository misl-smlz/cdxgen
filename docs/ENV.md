# Configuration

The following environment variables are available to configure the bom generation behavior.

| Variable                     | Description                                                                                                                          |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| CDXGEN_DEBUG_MODE            | Set to `debug` to enable debug messages                                                                                              |
| GITHUB_TOKEN                 | Specify GitHub token to prevent traffic shaping while querying license and repo information                                          |
| MVN_CMD                      | Set to override maven command                                                                                                        |
| MVN_ARGS                     | Set to pass additional arguments such as profile or settings to maven                                                                |
| MAVEN_HOME                   | Specify maven home                                                                                                                   |
| MAVEN_CENTRAL_URL            | Specify URL of Maven Central for metadata fetching (e.g. when private repo is used)                                                  |
| BAZEL_TARGET                 | Bazel target to build. Default :all (Eg: //java-maven)                                                                               |
| BAZEL_STRIP_MAVEN_PREFIX     | Strip Maven group prefix (e.g. useful when private repo is used, defaults to `/maven2/`)                                             |
| BAZEL_USE_ACTION_GRAPH       | SBOM for specific Bazel target, uses `bazel aquery 'outputs(".*.jar", deps(<BAZEL_TARGET>))'` (defaults to `false`)                  |
| GRADLE_CACHE_DIR             | Specify gradle cache directory. Useful for class name resolving                                                                      |
| GRADLE_MULTI_PROJECT_MODE    | Unused. Automatically handled                                                                                                        |
| GRADLE_ARGS                  | Set to pass additional arguments such as profile or settings to gradle (all tasks). Eg: --configuration runtimeClassPath             |
| GRADLE_ARGS_PROPERTIES       | Set to pass additional arguments only to the `gradle properties` task, used for collecting metadata about the project                |
| GRADLE_ARGS_DEPENDENCIES     | Set to pass additional arguments only to the `gradle dependencies` task, used for listing actual project dependencies                |
| GRADLE_HOME                  | Specify gradle home                                                                                                                  |
| GRADLE_CMD                   | Set to override gradle command                                                                                                       |
| GRADLE_DEPENDENCY_TASK       | By default cdxgen use the task "dependencies" to collect packages. Set to override the task name.                                    |
| SBT_CACHE_DIR                | Specify sbt cache directory. Useful for class name resolving                                                                         |
| FETCH_LICENSE                | Set this variable to `true` or `1` to fetch license information from the registry. npm and golang                                    |
| USE_GOSUM                    | Set to `true` or `1` to generate BOMs for golang projects using go.sum as the dependency source of truth, instead of go.mod          |
| CDXGEN_TIMEOUT_MS            | Default timeout for known execution involving maven, gradle or sbt                                                                   |
| CDXGEN_SERVER_TIMEOUT_MS     | Default timeout in server mode                                                                                                       |
| CLJ_CMD                      | Set to override the clojure cli command                                                                                              |
| LEIN_CMD                     | Set to override the leiningen command                                                                                                |
| SBOM_SIGN_ALGORITHM          | Signature algorithm. Some valid values are RS256, RS384, RS512, PS256, PS384, PS512, ES256 etc                                       |
| SBOM_SIGN_PRIVATE_KEY        | Private key to use for signing                                                                                                       |
| SBOM_SIGN_PUBLIC_KEY         | Optional. Public key to include in the SBoM signature                                                                                |
| CDX_MAVEN_PLUGIN             | CycloneDX Maven plugin to use. Default "org.cyclonedx:cyclonedx-maven-plugin:2.7.8"                                                  |
| CDX_MAVEN_GOAL               | CycloneDX Maven plugin goal to use. Default makeAggregateBom. Other options: makeBom, makePackageBom                                 |
| CDX_MAVEN_INCLUDE_TEST_SCOPE | Whether test scoped dependencies should be included from Maven projects, Default: true                                               |
| ASTGEN_IGNORE_DIRS           | Comma separated list of directories to ignore while analyzing using babel. The environment variable is also used by atom and astgen. |
| ASTGEN_IGNORE_FILE_PATTERN   | Ignore regex to use                                                                                                                  |
