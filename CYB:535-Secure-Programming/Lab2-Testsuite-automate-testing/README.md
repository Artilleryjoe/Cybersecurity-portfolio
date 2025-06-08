# Using a Test Suite to Automate Unit Testing

## Course  
CYB/535 – Secure Programming

## Objective  
This lab demonstrates how to automate testing of application functions using Python’s built-in `unittest` framework. Automated unit testing is a key component of secure software development, ensuring code reliability, reducing regressions, and supporting continuous integration.

## Tools Used  
- Python 3.x  
- PyCharm  
- `unittest` module

## Procedure  
- Open the existing project in PyCharm  
- Create a new file called `test_hashing.py`  
- Import the function and define unit tests:
  ```python
  import unittest
  from your_module import gen_pass_hash  # Adjust 'your_module' as needed

  class TestPasswordHashing(unittest.TestCase):

      def test_valid_input(self):
          result, hash_val = gen_pass_hash("TestPass123", "salt123")
          self.assertTrue(result)
          self.assertEqual(len(hash_val), 64)  # SHA-256 hash length

      def test_empty_password(self):
          result, _ = gen_pass_hash("", "salt123")
          self.assertTrue(result)

      def test_empty_salt(self):
          result, _ = gen_pass_hash("TestPass123", "")
          self.assertTrue(result)

      def test_invalid_input(self):
          result, _ = gen_pass_hash(None, None)
          self.assertFalse(result)

  if __name__ == '__main__':
      unittest.main()
- Run the test suite in PyCharm's test runner or from the terminal:
    ```bash
    python -m unittest test_hashing.py
- Observe pass/fail output and adjust the main function if needed

## Results
- All valid input tests passed as expected
- Invalid inputs triggered exception handling and returned failure
- Test suite provided a repeatable way to validate logic without manual input
- PyCharm’s integration allowed for easy debugging of test cases

## Lessons Learned
- Unit testing ensures that changes in logic do not introduce new bugs
- Testing edge cases (e.g., None, empty strings) helps validate input handling
- Automating tests increases development efficiency and reduces human error
- Integrating test suites into CI/CD pipelines improves overall code quality
