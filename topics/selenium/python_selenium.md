Notes from [Learning Selenium Testing Tools with Python](http://file.allitebooks.com/20160412/Learning%20Selenium%20Testing%20Tools%20with%20Python.pdf)

---

**Installing**

- `pip install -U selenium`
- or: [download](https://pypi.python.org/pypi/selenium) and `python setup.py install`

**Browse docs**

[link](http://selenium.googlecode.com/git/docs/api/py/api.html)

**IDEs**

- [JetBrains PyCharm](http://www.jetbrains.com/pycharm)
- [PyDev Eclipse plugin](http://pydev.org)
- [PyScripter](https://code.google.com/p/pyscripter)


**Example code**

[github link](https://github.com/upgundecha/learnsewithpython)

**Basics**

- load module  
```python
from selenium import webdriver
```
- create new firefox session  
```python
driver = webdriver.Firefox()
driver.implicitly_wait(30)
driver.maximize_window()
```
- navigate to page  
```python
driver.get('http://some.url')
```
- select DOM node  
```python
input = driver.find_element_by_name("input")
# will lookup name='input' attribute
```
- remove content from DOM node  
```python
input.clear
```
- add text to DOM node  
```python
input.send_keys('foo')
input.submit()
```
- get selection from DOM  
```python
items = driver.find_elements_by_xpath("//foo")
```
- print text of each node in selection  
```python
for item in items
  print item.text
```
- close browser window  
```python
driver.quit()
```

**Testing IE**

- download [InternetExplorerDriver server](http://www.seleniumhq.org/download)
- unzip and copy to working directory
- make sure Protected Mode is uniformly turned on or off
- initialize driver:  
```python
  dir = os.path.dirname(__file__)
  ie_driver_path = dir + "\IEDriverServer.exe"
  driver = webdriver.Ie(ie_driver_path)
```

**Testing Chrome**

- download [ChromeDriver](http://chromedriver.storage.googleapis.com/index.html)
- unzip and copy to working directory
- ininitialize driver:  
```python
dir = os.path.dirname(__file__)
chrome_driver_path = dir + "\chromedriver.exe"
# remove the .exe on linux or osx
driver = webdriver.Chrome(chrome_driver_path)
```

**Testing with `unittest`**

This is only tangentially related - see [sections/unittest.md]

**Selenium's DOM query methods**

All of these have a corresponding `find_elements` method

- `find_element_by_id(id)` uses id attribute
- `find_element_by_name(name)` uses name attribute
- `find_element_by_class(name)` uses class attribute
- `find_element_by_tag_name(name)`
- `find_element_by_xpath(path)`
- `find_element_by_css_selector(css_selector)`
- `find_element_by_link_text(link_text)`
- `find_eement_by_partial_link_text(link_text)`


**Xpath**

for more info, see [w3schools](http://www.w3schools.com/Xpath/) and
[a tutorial](http://www.zvon.org/comp/r/tut-XPath_1.html)

**The WebDriver class**

[reference](http://selenium.googlecode.com/git/docs/api/py/webdriver_remote/selenium.webdriver.remote.webdriver.html#moduleselenium.webdriver.remote.webdriver)

- `driver.current_url`
- `driver.current_window_handle`
- `driver.name` the type of browser being used
- `driver.orientation` for supported devices
- `driver.page_source`
- `driver.title`
- `driver.window_handles` al windows within the session
- `driver.back()` navigate back
- `driver.close()`
- `driver.forward()`
- `driver.get(url)`
- `driver.maximize_window()`
- `driver.quit()`
- `driver.refresh()`
- `driver.switch_to_active_element()` shows the element which is focused
- `driver.switch_to_alert()` shifts focus to alert
- `driver.switch_to_default_content()` shifts focus to default frame 
- `driver.switch_to_frame(frame_reference)` given index/name/web element/iframe
- `driver.switch_to_window(name)`
- `driver.implicity_wait(time_to_wait)` sets timeout (set once-per-session)
- `driver.set_page_load_timeout(time)` number of seconds to wait
- `driver.set_script_timeout(time)` number of seconds to wait

**WebElement class**

[reference](http://selenium.googlecode.com/git/docs/api/py/webdriver_remote/selenium.webdriver.remote.webelement.html#moduleselenium.webdriver.remote.webelement)

- `element.size`
- `element.tag_name`
- `element.text`
- `element.clear()`
- `element.click()`
- `element.get_attribute(name)`
- `element.is_displayed()` checks if it is visible to user
- `element.is_enabled` checks if the element is enabled
- `element.is_selected` i.e. for radios or checkboxes
- `element.send_keys(string)` simulates typing
- `element.submit()` can be called on a form or form's input
- `element.value_of_css_property(property_name)`

**Other methods**

- `click(element)`
- `click_and_hold(element)`
- `double_click(element)`
- `drag_and_drop(source, target)`
- `key_down(vaue, element)`
- `key_up(value, element)`
- `move_to_element(element)`
- `perform`
- `release(element)`
- `send_keys(keys)`
- `send_keys_to_element(element, keys)`
- [docs](http://selenium.googlecode.com/git/docs/api/py/webdriver/selenium.webdriver.common.action_chains.html)

**Executing Javascript**

- `execute_async_script(script, *args)`
- `execute_script(script, *args)`

**Screenshots**

- `driver.save_screenshot(filename)`
- `driver.get_screenshot_as_base64()`
- `driver.get_screenshot_as_file(name)`
- `driver.get_screenshot_as_png()`

**Cookies**

- `driver.add_cookie(hash)`
- `driver.delete_all_cookies()`
- `driver.delete_cookie(name)`
- `driver.get_cookie(name)`
- `driver.get_cookies()`

**Record video of test run**

use `Castro` python library (`pip install Castro`)

**Select class**

a special class to work with dropdowns and lists

[reference](http://selenium.googlecode.com/git/docs/api/py/webdriver_support/selenium.webdriver.support.select.html#moduleselenium.webdriver.support.select)

- _in the following, `element` refers to a `select` element
- `element.all_selected_options`
- `element.first_selected_option`
- `element.options`
- `element.deselect_all()`
- `element.deselect_by_index(index)`
- `element.deselect_by_value(value)`
- `element.deselect_by_visible_text(text)`
- `element.select_by_index(index)`
- `element.select_by_value(value)`
- `element.select_by_visible_text(text)`


**Working with alerts and pop-up windows**

There is a special Alert class for dealing with alert windows

- `alert.text`
- `alert.accept()`
- `alert.dismiss()`
- `alert.send_keys(string)`


**Explicit wait**

This is a more fine-tuned approach than implicit wait.

[reference](http://selenium.googlecode.com/git/docs/api/py/webdriver_support/selenium.webdriver.support.expected_conditions.html#moduleselenium.webdriver.support.expected_conditions)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions
import unittest
```

```python
WebDriverWait(self.driver, 10).until(
  expected_conditions.element_to_be_clickable((By.NAME, "some_name"))
)
# this is an example of a "locator" argument (the part using By.NAME)
```

Other "expected conditions" methods

- `element_to_be_selected(element)` wait for element to be selected
- `invisibility_of_element_located(locator)` wait for element to be hidden
- `presence_of_all_elements_located(locator)` waits for an element in the locator
- `presence_of_element_located(locator)`
- `text_to_be_present_in_element(locator, text)`
- `title_contains(title)`
- `title_is(title)`
- `visibility_of(element)`
- `visibility_of_element_located(locator)`

Using a lambda condition

```python
WebDriverWait(self.driver, 10).until(lambda s: s.find_element_by_id("foo").text == "bar")
```

**Using an external server to run tests**

- download standalone server from [here](http://docs.seleniumhq.org/download/)
- run the server with `java –jar selenium-server-standalone-2.41.0.jar`
- open `http://<remote-machine-ip>:4444/wd/hub/static/resource/hub.html`
- specify platform  
```python
desired_caps = {}
desired_caps['platform'] = 'WINDOWS'
desired_caps['browserName'] = 'firefox'
self.driver = webdriver.Remote("http://192.168.1.103:4444/wd/hub,
desired_caps")
```
- to add support for IE  
```bash
java -Dwebdriver.ie.driver=“C:\SeDrivers\IEDriverServer.exe” -jar seleniumserver-standalone-2.41.0.jar
```
- to add support for Chrome  
```bash
java -Dwebdriver.ie.driver=“C:\SeDrivers\IEDriverServer.exe” -
Dwebdriver.chrome.driver=“C:\SeDrivers\chromedriver.exe” -jar seleniumserver-standalone-2.41.0.jar
```
- use [json wire protocol](https://code.google.com/p/selenium/wiki/JsonWireProtocol) to run distributed tests  
```bash
# start hub
java -jar selenium-server-standalone-2.25.0.jar -port 4444 -role hub
```

**Appium client**

`pip install Appium-Python-Client`

[docs](https://pypi.python.org/pypi/Appium-Python-Client)

**Data-driven tests**

`pip instal ddt`
