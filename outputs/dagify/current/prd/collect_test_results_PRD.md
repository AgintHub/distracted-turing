# collect_test_results PRD

## Description
Gathers, processes, and consolidates raw test execution outputs, including detailed logs, error messages, and performance metrics from the test run, providing a comprehensive test result summary.


## Conceptual Info

This node aggregates and documents test execution outputs to facilitate analysis and reporting, providing insights into test effectiveness, performance, and reliability.

## Docstring

### Summary
Collects and processes test execution outputs, including logs, errors, and performance metrics, and returns them in a structured format.

### Parameters

- **test_run_id** (str): Unique identifier for the test run.

### Returns

dict: A dictionary containing the collected test execution outputs, including logs, errors, and performance metrics.

### Raises

- TestRunNotFoundError: Raised when the specified test run ID is not found.

### Examples

```python
>>> test_run_id = 'TR-123'
>>> results = collect_test_results(test_run_id)
>>> print(results['execution_logs'])
['2023-02-20 14:30:00 INFO: Test started', '2023-02-20 14:30:05 ERROR: Test failed']
```
