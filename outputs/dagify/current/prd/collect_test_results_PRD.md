# collect_test_results PRD

## Description
Aggregates raw execution logs, error traces, and performance metrics from a test run, categorizes and aggregates the data, and provides a concise summary for quick insight.


## Conceptual Info

The collect_test_results node functions as the central intelligence layer of the testing pipeline, transforming low‑level execution artefacts into a coherent, actionable knowledge base. By systematically normalising logs, classifying failures, and summarising performance, it enables downstream reporting, root‑cause analysis, and continuous improvement initiatives.

## Docstring

### Summary
Aggregates and normalises test execution artifacts into a structured report.

### Parameters

- **test_output** (dict): Dictionary containing raw logs, error traces, and metric snapshots produced by the test harness.

### Returns

dict: A dictionary with keys 'execution_logs', 'error_messages', 'performance_metrics', and 'log_summary' as described in the output structure.

### Raises

- ValueError: Raised if the input dictionary lacks required keys or contains malformed data.

### Examples

```python
>>> from collect_test_results import collect_test_results
>>> result = collect_test_results(test_output)
>>> print(result['log_summary'])
"3 errors encountered: 2 AssertionErrors, 1 TimeoutError. Average response time 120.4ms exceeded the 100ms threshold."
```
