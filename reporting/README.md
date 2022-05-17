# Test Result Reporting

## Environment Setup

To build and run the test reporting, first install and run either [miniconda](https://docs.conda.io/en/latest/miniconda.html) or full [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)


Once that is installed, you can create the reporting environment with the following command:

```bash
$ conda env create -f environment.yml python=3.9
```


And then activate it:

```bash
$ conda activate reporting
```

## Run reporting

The reporter can be run with the following command:

```bash
$ ./reporter.py
```

It will automatically fetch the latest interop test results, process them, and launch a server hosting the dashboard at [http://localhost:8050/](http://localhost:8050/)

Test results are sourced from the JSON test results published here:

[https://w3c-ccg.github.io/traceability-interop/reports/](https://w3c-ccg.github.io/traceability-interop/reports/)


To get a list of reporter options, you can execute the reporter with the help parameter:
```bash
$ ./reporter.py -h
usage: reporter.py [-h] [--mode [{all,data,html,dashboard}]]

Interop test results reporting utility

optional arguments:
  -h, --help            show this help message and exit
  --mode [{all,data,html,dashboard}]
                        mode to run the reporter in
```


## Next steps and end goals

There are three main modules:

- `./postman_reporter/report_data.py` — go get the data, link it up, create appropriate data frames, and store them as CSV for easy use
- `./postman_reporter/report_static.py` — generate a static HTML report for use with gh-pages (IN-PROGRESS)
- `./postman_reporter/report_dashboard.py` — the latter half of this app that spins up a dash app on flask for actually working with the test results
- `reporter.py` — the main binary that runs one or more modules as listed above, based on command line arguments 