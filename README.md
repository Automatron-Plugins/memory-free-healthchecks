# Memory Utilization Health Check

Nagios compatible Memory Utilization health check script for Automatron

## Install

Simply copy the `memfree.py` script to the `plugins/checks/` directory

## Usage

The `memfree` health check is used to check whether the available memory on a system is within threshold.

### OS Support

  * Linux
    * Debian Base (Debian, Ubuntu, etc.)
    * RedHat Base (RHEL, CentOS)
  * FreeBSD

For Linux systems this check script does take into consideration the memory used for cache and Linux's ability to reclaim that memory.

## Runbook example

The below is an example of the `memfree` check used within a runbook.

```yaml
checks:
  memfree:
    execute_from: target
    type: plugin
    plugin: memfree.py
    args: --warn=20 --critical=10
```

In the above, the health check will return a `WARNING` status if the memory is below `20%` and return a `CRITICAL` status if the memory is below `10%`.

### Required Arguments

The `memfree` check requires 2 arguments.

```yaml
args: --warn=<warning threshold %> --critical=<critical threshold %>
```

