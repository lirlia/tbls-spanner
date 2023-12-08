# Generate TBLs Documentation from Spanner DDL GitHub Action

This GitHub Action is designed to automatically generate documentation for database schemas defined in Spanner DDL (Data Definition Language) files. It utilizes the `tbls` tool to create comprehensive and readable documentation from the DDL.

## Inputs

| Input Name          | Description                               | Required | Default           |
|---------------------|-------------------------------------------|----------|-------------------|
| `tbls_args`         | Arguments to pass to the `tbls` command   | No       | `doc --rm-dist`   |
| `tbls_output_path`  | Output path for the generated documentation| No       | `docs/tbls`       |
| `ddl_path`          | Path to the Spanner DDL file              | Yes      | -                 |
| `google_project`    | Google Cloud project name                 | No       | `project`         |
| `spanner_instance`  | Spanner instance name                     | No       | `instance`        |
| `spanner_database`  | Spanner database name                     | No       | `database`        |
| `timeout`           | Timeout                                   | No       | `60`(sec)         |

## Usage

To use this action, include it in your workflow YAML file with the necessary inputs. For example:

```yaml
jobs:
  generate-docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: lirlia/tbls-spanner@latest
        with:
          ddl_path: 'path/to/your/ddl.sql'
          # Specify other inputs as needed
```

### use own .tbls.yml

```yaml
jobs:
  generate-docs:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: lirlia/tbls-spanner@latest
        with:
          ddl_path: 'path/to/your/ddl.sql'
          tbls_args: 'doc --config path/to/your/.tbls.yml'
          tbls_output_path: ''
```

## Conclusion

This GitHub Action simplifies the process of generating documentation from Spanner DDL files, making it easier for teams to maintain up-to-date documentation of their database schemas.
