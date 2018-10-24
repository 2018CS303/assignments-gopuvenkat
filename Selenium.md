# Selenium

## Setup

1. Install a Selenium supported WebDriver to a web browser. Here, we shall work with `Firefox` browser.

Assuming that the path `~/.local/bin` is the execution `PATH`, here's how you would install the Firefox Web Driver, called geckodriver, on a Linux machine

```shell
wget https://github.com/mozilla/geckodriver/releases/download/v0.19.1/geckodriver-v0.19.1-linux64.tar.gz
tar xvfz geckodriver-v0.19.1-linux64.tar.gz
mv geckodriver ~/.local/bin
```

2. Install selenium package.

```shell
pip install selenium
```

3. Test

```python
from selenium import webdriver

driver = webdriver.Firefox()
driver.get('https://github.com')

# driver.title
# 'The world’s leading software development platform · GitHub'

assert 'GitHub' in driver.title

assert 'GitLab' in driver.title                                 # Assertion Error

driver.quit()
```

4. Test driving a Headless Browser

A headless browser is just a regular web browser, except that it contain no visible UI element. It can make requests, also render HTML, keep session information and even perform asynchronous network communications by running JavaScript code.

```python
from selenium import webdriver

options = webdriver.FirefoxOptions()
options.add_argument('--headless')
driver  = webdriver.Firefox(options = options)

driver.get('https://github.com/')

# driver.title
# 'The world’s leading software development platform · GitHub'

assert 'GitHub' in driver.title

assert 'GitLab' in driver.title                                 # Assertion Error

driver.quit()
```
