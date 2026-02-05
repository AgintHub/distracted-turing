# create_test_cases PRD

## Description
Generates a complete, structured list of test cases derived from the defined test scope, ensuring coverage of all objectives, constraints, and success criteria.


## Conceptual Info

This node translates high‑level test goals and constraints into actionable, traceable test cases that can be directly executed by QA teams or automated frameworks. It ensures that every requirement is validated, reduces ambiguity, and provides a clear audit trail from scope to execution.

## Docstring

### Summary
Create detailed test case descriptions from a test scope definition.

### Parameters

- **scope_json** (dict): Dictionary containing 'goals', 'boundaries', 'success_criteria', and 'summary' keys as produced by identify_test_scope.

### Returns

tuple[List[str], int]: A tuple containing the list of test case descriptions and the total count.

### Raises

- ValueError: Raised when required keys are missing or malformed in the input scope.

### Examples

```python
>>> scope = {
...     "goals": ["Verify login", "Ensure data persistence"],
...     "boundaries": ["Maximum input length", "Null value handling"],
...     "success_criteria": ["Login succeeds in 2s", "Data remains after restart"],
...     "summary": "Login and persistence test scope."
>>> }
>>> test_cases, count = create_test_cases(scope)
['Test 1: Valid login within 2s using standard credentials.', 'Test 2: Verify data persistence after application restart.']
2
```
