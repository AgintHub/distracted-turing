# analyze_test_results PRD

## Description
Assess test outcomes against criteria


## Conceptual Info

The node evaluates the raw test execution data produced by the test framework, compares each test case's actual outcome to its expected result, and aggregates the results into a concise report. It provides an objective pass/fail assessment of the entire test suite without offering remediation suggestions.

## Docstring

### Summary
Analyze test results and produce an objective pass/fail summary.

### Parameters

- **execution_logs** (List[str]): Raw log entries captured during test execution, one per test case.
- **error_messages** (List[str]): Error messages or exception traces associated with each test case.
- **performance_metrics** (List[float]): Numeric performance measurements (e.g., response times) for each test case.
- **log_summary** (str): A brief textual summary of the collected logs and errors.

### Returns

Dict[str, Any]: A dictionary containing the following keys:
- summary (str): A short narrative of overall test outcomes.
- total_tests (int): Number of test cases processed.
- passed_tests (int): Number of test cases that passed.
- failed_tests (int): Number of test cases that failed.
- failed_test_ids (List[str]): Identifiers of failed test cases.
- overall_pass (bool): True if every test passed, otherwise False.

### Raises

- ValueError: If any of the input lists are of mismatched lengths or empty.

### Examples

```python
>>> result = analyze_test_results(
...     execution_logs=["TC1 PASS", "TC2 FAIL"],
...     error_messages=["", "AssertionError: expected 200 but got 500"],
...     performance_metrics=[0.12, 0.15],
...     log_summary="2 tests executed, 1 failure."
>>> )
{'summary': '1 failure out of 2 tests.', 'total_tests': 2, 'passed_tests': 1, 'failed_tests': 1, 'failed_test_ids': ['TC2'], 'overall_pass': False}
```

```python
>>> result = analyze_test_results(
...     execution_logs=["TC1 PASS", "TC2 PASS"],
...     error_messages=["", ""],
...     performance_metrics=[0.10, 0.08],
...     log_summary="2 tests executed, no failures."
>>> )
{'summary': 'All tests passed.', 'total_tests': 2, 'passed_tests': 2, 'failed_tests': 0, 'failed_test_ids': [], 'overall_pass': True}
```
