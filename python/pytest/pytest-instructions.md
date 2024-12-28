# Testing Instructions for Python Projects

These instructions provide guidelines for writing effective and maintainable tests for any Python project, regardless of the specific frameworks or libraries used. The aim is to ensure that the code is robust, reliable, and easy to maintain.

## Core Principles

*   **Test Early and Often:** Write tests alongside your code and run them frequently during development.
*   **Test-Driven Development (TDD):**  Consider adopting TDD by writing tests *before* writing the code.
*   **Test Pyramid:** Prioritize unit tests, followed by integration tests, and finally end-to-end or UI tests.
*   **Clear and Concise Tests:** Keep your test code simple, focused, and easy to understand.
*   **Comprehensive Coverage:** Strive for good test coverage to ensure all critical code paths and edge cases are tested.
*   **Maintainable Tests:** Write modular, reusable test code that is easy to update and refactor.
*   **Automation:** Automate your tests as much as possible, and run them on every commit/pull request using a CI/CD pipeline.

## Testing Framework

*   **Preferred Framework:** Use `pytest` as the primary testing framework. `pytest` is preferred due to its simplicity, powerful features, extensive plugins, and automatic test discovery.

## Test Structure

*   **Test Discovery:** `pytest` automatically discovers tests using the following conventions:
    *   Test files should be named `test_<module_name>.py` or `<module_name>_test.py` (e.g., `test_my_module.py`, `my_module_test.py`).
    *   Test functions should be named `test_<feature_name>()` (e.g., `test_addition()`, `test_validation_failure()`).
    *   Place test files in a dedicated `tests/` directory, or within the same directories as your code.
*   **Arrange-Act-Assert (AAA):**  Structure your tests using the Arrange-Act-Assert pattern:
    *   **Arrange:** Set up the test environment (e.g., create objects, configure data).
    *   **Act:** Execute the code or function you are testing.
    *   **Assert:** Verify the outcome by using `pytest`'s assertion methods (e.g., `assert value == expected`, `assert isinstance(obj, type)`).

## Testing Techniques

*   **Fixtures:** Use `pytest` fixtures to create reusable setup and teardown code.
    *   Define fixtures with the `@pytest.fixture` decorator.
    *   Fixtures are defined in a `conftest.py` or test files
    *   Use fixtures for dependencies, common resources, and test data creation.
*   **Parametrization:** Use `pytest.mark.parametrize` to run the same test multiple times with different inputs and expected outcomes.
*   **Markers:** Use markers (`@pytest.mark.slow`, `@pytest.mark.integration`, etc.) to categorize tests for selective running.
*   **Mocks and Stubs:** Use mocking libraries (e.g., `unittest.mock`, `pytest-mock`) to isolate the unit under test by replacing dependencies with controlled substitutes. This is essential for avoiding external dependencies when testing.
*   **Exception Handling:** Test expected exceptions using `pytest.raises`.
*   **Test Data Management:**
    *   Create clear and organized test data.
    *   Consider using fixtures or data files for test data input.
*   **Logging:** Do not add logging during test function execution. Any log data should be handled by fixtures.

## Specific Testing for Various Python Libraries

*   **Django:**
    *   Use `pytest-django` for integrating `pytest` with Django projects.
    *   Use Django's `TestCase` for database interaction in tests.
    *   Test views by simulating requests and checking responses.
    *   Use fixtures to manage test database states.
*   **FastAPI and Flask:**
    *   Use a test client or similar to send requests and verify responses.
    *   Mock dependencies to test specific code parts of the API endpoint logic.
*   **Selenium:**
    *   Use Selenium to test the user interface of your web applications.
    *   Use fixtures to manage browser sessions.
    *   Test elements, actions, and expected UI behavior.
*   **Keras, TensorFlow, PyTorch:**
    *   Test model behavior and model creation process.
    *   Test training routines and validation data
    *   Mock functions to avoid intensive model training during testing.
    *   Test with a small sample of data for efficiency.
    *   Test data pre-processing and input pipelines.
*   **NumPy and Pandas:**
    *   Test functions with different input arrays and dataframes.
    *   Test correct handling of different data types and shapes.
    *   Test expected output arrays and dataframes.
    *   Test edge cases such as empty data or different data types.

## Test Types

*   **Unit Tests:** Focus on testing individual functions, classes, or methods. These should be fast, isolated, and comprehensive.
*   **Integration Tests:** Verify the interaction between multiple units or modules. These tests ensure that various components work together correctly.
*   **End-to-End (E2E) / UI Tests:**  Verify the complete user experience, including the user interface and all components.

## Test Reporting and Automation

*   **Reporting:**  `pytest` generates detailed reports. Customize the report output as required.
*   **Automation:** Integrate tests into your CI/CD pipelines to ensure tests are automatically run on code changes.

## General Test Best Practices

*   Write clear, descriptive test names that clearly state what is being tested.
*   Test edge cases, boundary conditions, and error scenarios.
*   Keep tests focused on testing a single unit of code or a specific functionality.
*   Refactor your test code when necessary to keep it clean and maintainable.
*   Keep test code and production code separate.

## Dependencies

*   pytest
*   (Any dependencies specific to a particular type of testing e.g., pytest-django, pytest-mock, selenium)


## Adherence

*   Enforce these guidelines using linters and formatters in your project's CI/CD pipeline.
