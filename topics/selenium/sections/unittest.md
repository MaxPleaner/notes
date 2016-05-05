**Unit Testing with `unittest`**

- [docs](http://docs.python.org/2/library/unittest.html)
- tests are organized into 3 parts:
  - _arrange_: initial state
  - _act_: execute
  - _assert_: check outcome
- write a test:  
```python
import unittest
class MyTest(unittest.TestCase):
  def setUp(self)
    self.driver = webdriver.Firefox()
  def tearDown(self)
    self.driver.quit()
  def testCase(self)
    self.assertEqual(2, 2)
```zzz
- run a test:  
```python
if __name__ == `__main__`:
  unittest.main(verbosity=2)
```
- share setup state  
```python
class MyTests(unit.TestCase):
  @classmethod
  def setUpClass(cls)
    cls.driver = webdriver.Firefox()
    cls.driver.get("http://some.url")
  @classmethod
  def tearDownClass(cls)
    cls.driver.quit()
```
- [more info on `@classmethod`](https://docs.python.org/2/library/functions.html#classmethod)
- types of assertions (most take an optional additional argument which is an error msg)
  - `assertEqual(a, b)`
  - `assertNotEqual(a, b)`
  - `assertTrue(x)`
  - `assertFalse(x)`
  - `assertIsNot(a, b)`
  - `assertRaises(exc, fun, *args, **kwds)`
  - `assertRaisesRegexp(exc, r, fun, *args, **kwds)`
  - `assertAlmostEqual(a, b)`
  - `assertNotAlmostEqual(a, b)`
  - `assertGreater(a, b)`
  - `assertGreaterEqual(a, b)`
  - `assertLess(a, b)`
  - `assertLessEqual(a, b)`
  - `assertRegexpMatches(s, r)`
  - `assertNotRegexMatches(s, r)`
  - `assertMultiLineEqual(a, b)`
  - `assertListEqual(a, b)`
  - `fail()`
- test suites  
```python
import unittest
from selenium import webdriver
from seleniumcommon.exceptions import NoSuchElementException
from selenium.webdriver.common.by import By
from __builtin__ import classmethod
from mytestfile import MyTests
from myothertestfile import MyOtherTests
my_tests = unittest.TestLoader().loadTestsFromTestCase(MyTests)
my_other_tests = unittest.TestLoader().loadTestsFromTestCase(MyOtherTest)
all_tests = unittest.TestSuite([my_tests, my_other_tests])
unittest.TextTestRunner(verbosity=2).run(all_tests)
class MyTest(unittest.TestCase):
```

**HTML test reports**

[HTMLTestRunner](http://pypi.python.org/pypi/HTMLTestRunner)

example:  
```python
import unittest
import HTMLTestRunner
import os
from my_tests import MyTests
from my_other_tests import MyOtherTests
my_tests = unittest.TestLoader().loadTestsFromTestCase(MyTests)
my_other_tests = unittest.TestLoader().loadTestsFromTestCase(MyOtherTests)
all_tests = unittest.TestSuite([my_tests, my_other_tests])
outfile = open(dir + "\MyTestReport.html", 'w')
runner = HTMLTestRunner.HTMLTestRunner(
  stream=outfile,
  title='Test Report',
  description = "MyTests"
)
runner.run(all_tests)
dir = os.getcwd()

```
