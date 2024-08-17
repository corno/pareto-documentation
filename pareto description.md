This is a pareto project.

# Initialization

run ./scripts/initialize.sh from the root of the project

This sets up the build environment

# Build

run ./scripts/scripts/buildFromScratch.sh

# Directory Structure

Pareto projects adhere to a very strict directory structure. During the build phase this directory structure is validated.

The directory structure is a mix of generated files and handwritten files.

- scripts

        all callable scripts. All generated. Manual changes will be ignored/overwritten
- pareto

        Define the project configuration and the API here. After everything is configured, the skeleton typescript code can be generated. 

- .gitignore 

    this file is generated
-typescript

    Here is the source code

scripts/
pareto/
.gitignore
typescript/
    pub
    test

# Setting up a new project

# API

there is a set of core libraries.

## pareto-core-lib

this library mimics language features that are not supported by TypeScript

# Setting up a new project

- create a directory
- in this directory, create a directory named 'scripts'.
- in the 'scripts' directory, create an executable file named 'initialize.sh' and with this content:
    ```
    #!/usr/bin/env bash

    paretoBuildEnvDir=`realpath $(dirname "$0")`

    "$paretoBuildEnvDir/node_modules/pareto-buildenvironment/initializeProject.sh" "$paretoBuildEnvDir/.."
    ```
- make it executable: 'chmod +x initialize.sh'
- in the 'scripts' directory install the node module 'pareto-buildenvironment' ('npm install pareto-buildenvironment')
- in root directory, type './scripts/initialize.sh', the 'scripts' directory should now be populated
- in the root directory, type './scripts/scripts/buildFromScratch.sh', a directory structure should now be scaffolded, and you will be presented with errors because files are missing. These you will need to add manually.
-the first file to add is '/pareto/src/data/project.data.ts' with this content: [project definition](./templates/pareto%20definition.ts)
    ```
    import * as pd from 'pareto-core-data'

    import * as mproject from "lib-pareto-typescript-project/dist/submodules/project"

    const d = pd.d

    import { } from "lib-pareto-typescript-project/dist/submodules/project/shorthands"


    export const $: mproject.T.Project<pd.SourceLocation> = {
        'author': "TBD",
        'description': "TBD",
        'license': "TBD",

        'dependencies': d({
        }),
        'type': ['library', {
            'main': {
                'definition': {
                    'glossary': {
                        'root': {
                            'glossary parameters': d({}),
                            'imports': d({
                            }),
                            'root': {
                                'namespaces': d({}),
                                'types': d({
                                }),
                            },
                            'asynchronous': {
                                'interfaces': d({
                                }),
                                'algorithms': d({
                                }),
                            },
                            'synchronous': {
                                'interfaces': d({}),
                                'algorithms': d({
                                }),
                            },
                        },
                        'imports': d({
                        }),
                    },
                    'api': {
                        'root': {
                            'algorithms': d({

                            }),
                        },
                        'imports': d({
                        }),
                    }
                },
                'implementation': ['typescript', null],
            },
            'submodules': d({
            }),
            'bindings': [true, {
                'definition': {
                    'glossary': {
                        'root': {
                            'glossary parameters': d({}),
                            'imports': d({
                            }),
                            'root': {
                                'namespaces': d({}),
                                'types': d({
                                }),
                            },
                            'asynchronous': {
                                'interfaces': d({}),
                                'algorithms': d({
                                }),
                            },
                            'synchronous': {
                                'interfaces': d({}),
                                'algorithms': d({}),
                            },
                        },
                        'imports': d({
                        }),
                    },
                    'api': {
                        'root': {
                            'algorithms': d({
                            }),
                        },
                        'imports': d({
                        }),
                    },
                },
                'implementation': ['typescript', null]

            }],
            'executables': d({}),
            'test': {
                'dependencies': d({
                    "res-pareto-build": null,
                }),
                'definition': {
                    'glossary': {
                        'root': {
                            'glossary parameters': d({}),
                            'imports': d({}),
                            'root': {
                                'namespaces': d({}),
                                'types': d({}),
                            },
                            'asynchronous': {
                                'interfaces': d({}),
                                'algorithms': d({}),
                            },
                            'synchronous': {
                                'interfaces': d({}),
                                'algorithms': d({}),
                            },
                        },
                        'imports': d({}),
                    },
                    'api': {
                        'root': {
                            'algorithms': d({}),
                        },
                        'imports': d({}),
                    },
                },
                'imports': d({}),
            },
        }],
    }
    ```

