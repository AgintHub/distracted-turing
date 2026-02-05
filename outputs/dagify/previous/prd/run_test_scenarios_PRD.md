# run_test_scenarios PRD

## Description
Execute all defined test cases


## Conceptual Info

The run_test_scenarios node is responsible for orchestrating the execution of every test case defined in the test suite. It leverages the environment prepared by execute_test_setup, runs each test case sequentially, captures the raw logs, determines pass/fail status based on exit codes or assertions, and records the execution time for performance analysis.

## Docstring

### Summary
Run all test cases and return raw execution data.

### Parameters

- **environment_id** (str): Unique identifier of the prepared test execution environment returned by execute_test_setup.
- **test_cases** (List[str]): A list of test case identifiers or script paths to be executed.
- **setup_steps** (List[str]): Ordered list of configuration actions performed during setup, used for contextual logging.

### Returns

Dict[str, List[Any]]: A dictionary containing four keys: 'test_case_ids', 'execution_status', 'execution_logs', and 'execution_times_seconds', each a list aligned by test case order.

### Raises

- RuntimeError: If the environment is not ready or a critical setup step failed.
- FileNotFoundError: If a specified test case file is missing.
- Exception: For any unexpected errors during test execution.

### Examples

```python
>>> result = run_test_scenarios(
...     environment_id='env_123',
...     test_cases=['tc1.sh', 'tc2.sh'],
...     setup_steps=['install deps', 'configure network']
>>> )
>>> print(result['execution_status'])
[True, False]
```

```python
>>> result = run_test_scenarios(
...     environment_id='env_456',
...     test_cases=['tc3.py'],
...     setup_steps=['setup env']
>>> )
>>> print(result['execution_times_seconds'])
[2.34]
```
