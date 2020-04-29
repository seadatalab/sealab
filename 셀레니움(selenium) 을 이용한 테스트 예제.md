# selenium 자동화 테스트
- 반복적인 테스트 수행의 시간절약
- 지치지 않는다
- 더 많이 테스트한다
- 더 견고한 테스트가 만들어 질것이다.

```
from selenium import webdriver
import sys
import time
import datetime

FILE_PATH = "/home/kimsk/ggdb/src/test"  
driver = webdriver.Chrome()


driver.maximize_window()

main_window = driver.current_window_handle

# 암묵적으로 웹 자원 로드를 위해 3초까지 기다려 준다.
driver.implicitly_wait(3)

url = "http://localhost:8080"

driver.get(url)

driver.find_element_by_link_text('LOGIN').click()

# login 실패
driver.find_element_by_xpath("//input[@type='email']").send_keys( 아이디 )
driver.find_element_by_xpath("//input[@type='password']").send_keys( 페스워드 )
not_ok = driver.find_element_by_id('login').click()

time.sleep(1)
alert = driver.switch_to_alert()
alert.accept()

time.sleep(1)

driver.find_element_by_id('home').click()
driver.find_element_by_link_text('LOGIN').click()
driver.find_element_by_xpath("//input[@type='email']").send_keys( 아이디 )
driver.find_element_by_xpath("//input[@type='password']").send_keys( 페스워드 )
driver.find_element_by_id('login').click()

time.sleep(2)
driver.close()
```
