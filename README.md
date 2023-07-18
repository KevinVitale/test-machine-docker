## Step 1: get an API key

Login with (or create) a **TestMachine** account [on the website](https://testmachine.ai/signup).

Copy [the API key shown](https://testmachine.ai/docs#get-api-key); set your API key in the `.env` file:

```
TM_TOKEN_KEY=
```

## Step 2: build the container

The _Docker_ container needs to be created at least once. With _Docker_ running on your system, execute the `build-cli.sh` script:
```
$ ./build-cli.sh
```

## Step 3: run the CLI

The cli can be run from within a _Docker_ container by executing `cli.sh`:

```
$ ./cli.sh

Usage: testmachine [options] [command]

TestMachine AI's CLI. Analyze smart contracts.

Options:
  -V, --version                  output the version number
  -v|--verbose                   Enable verbose logging.
  -o|--output <outputFormat>     Set result output type. Currently supported formats: json
  -t|--token <tokenOrTokenPath>  The API token to use. This can be either a file path or a string
  -h, --help                     display help for command

Commands:
  repo [options] <action>        Manage repositories.
  snapshot [options] <action>    Manage snapshots.
  analyses [options] <action>    Manage analyses.
  help [command]                 display help for command
```

All commands are available by simply appending the actions to the script invocation:

```
$ ./cli.sh repo list

Repositories:
┌─────────┬─────┬───────────┬────────────────────────────┬─────────────┬────────────┐
│ (index) │ ID  │   Name    │         Created at         │ # snapshots │ # analyses │
├─────────┼─────┼───────────┼────────────────────────────┼─────────────┼────────────┤
│    0    │ ### │ 'demorun' │ '2023-07-17T20:14:18.474Z' │      0      │     0      │
└─────────┴─────┴───────────┴────────────────────────────┴─────────────┴────────────┘
```

## Appendix: syncing files to the container

A local volume, a `data` folder in the current working directory, is mounted within the container to `/data`.
