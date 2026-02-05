# generate_test_data PRD

## Description
Create required test input datasets


## Conceptual Info

The generate_test_data node is responsible for producing all data files that will be consumed by test cases. It synthesizes data that match the structure, volume, and constraints defined in the test cases and the prepared environment. The node ensures that each file has the correct schema, data type fidelity, and that the overall dataset passes validation checks before signaling readiness to the test setup phase.

## Docstring

### Summary
Generate synthetic or curated test data needed for all test cases, ensuring compatibility with the prepared test environment and test case requirements.

### Parameters

- **test_cases** (List[str]): List of test case descriptions produced by the create_test_cases node. Each description may include data specifications such as field names, types, ranges, and expected record counts.
- **environment_config** (Dict[str, Any]): Dictionary of environment settings output from the prepare_test_environment node, such as supported file formats, database connection parameters, and any constraints on data content.

### Returns

Dict[str, Any]: A dictionary matching the output_structure of the node: keys "test_data_files", "record_counts", "data_formats", and "is_valid".

### Raises

- ValueError: Raised if any test case specification is malformed or missing required fields.
- RuntimeError: Raised if data generation fails due to unsupported format, insufficient resources, or validation errors.

### Examples

```python
>>> test_cases = ["Test case 1: 1000 CSV rows", "Test case 2: 500 JSON objects"],
>>> environment_config = {"supported_formats": ["CSV", "JSON"]},
>>> result = generate_test_data(test_cases, environment_config)
{
  "test_data_files": ["tc1_data.csv", "tc2_data.json"],
  "record_counts": [1000, 500],
  "data_formats": ["CSV", "JSON"],
  "is_valid": true
}
```

```python
>>> test_cases = ["Test case 3: 2000 XML rows"],
>>> environment_config = {"supported_formats": ["CSV", "JSON"]},
>>> try:
  generate_test_data(test_cases, environment_config)
except RuntimeError as e:
  print(e)
"RuntimeError: Unsupported data format 'XML' for test case 3"
```
