# generate_test_report PRD

## Description
Create formal test evaluation summary


## Conceptual Info

The node synthesizes a formal, objective test report by consuming the high‑level outcome metrics produced by the analysis step. It distills the raw test statistics into human‑readable sections that describe what was tested, how it was tested, the factual outcome, and the overall pass/fail decision.

## Docstring

### Summary
Generate a concise, objective test report from analysis results.

### Parameters

- **summary** (str): Brief textual summary of the analysis highlighting overall findings.
- **total_tests** (int): Total number of test cases evaluated.
- **passed_tests** (int): Count of test cases that met expected outcomes.
- **failed_tests** (int): Count of test cases that did not meet expected outcomes.
- **failed_test_ids** (List[str]): Identifiers or names of the test cases that failed.
- **overall_pass** (bool): Overall pass/fail status of the test run (true if all tests passed).

### Returns

dict: A dictionary containing the formatted test report fields: test_scope, test_procedures, results_analysis, overall_status.

### Raises

- ValueError: If any input is of an unexpected type or value.

### Examples

```python
>>> report = generate_test_report(
...     summary='All functional tests executed',
...     total_tests=15,
...     passed_tests=14,
...     failed_tests=1,
...     failed_test_ids=['TC-07'],
...     overall_pass=False)
>>> print(report['results_analysis'])
"Detected 1 failed test(s) out of 15: TC-07. Overall status: Fail."
```

```python
>>> report = generate_test_report(
...     summary='Security tests completed',
...     total_tests=8,
...     passed_tests=8,
...     failed_tests=0,
...     failed_test_ids=[],
...     overall_pass=True)
>>> print(report['overall_status'])
True
```
