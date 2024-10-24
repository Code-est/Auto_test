Exe’шник для тестирования https://tools.mega8.ru/numbers/amount.php.
Exe’шник использует библиотеки selenium, time, random.
Exe’шник: 
1)	автоматически открывает сайт и находит соответствующее окно для ввода (теста);
2)	вводит числовые значения от 0 и 0 до 10 000 с рандомным интервалом от 1 до 10;
3)	вводит одно рандомное числовое значение с плавающей запятой (точкой);
4)	вводит числа от 10 до 10**80, добавляя к числу 0 после каждого ввода;
5)	автоматически находит и нажимает кнопку подсчёта



from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.keys import Keys
import time
import random
 
driver = webdriver.Chrome()
driver.get("https://tools.mega8.ru/numbers/amount.php") 
time.sleep(1)

driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/textarea").click()
time.sleep(1)

action = ActionChains(driver)
action.key_down(Keys.CONTROL).send_keys('a').perform()
action.key_down(Keys.BACKSPACE).perform()
time.sleep(1)

driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/textarea").send_keys('\n0')
driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/textarea").send_keys('\n0')
for i in range(0,10000, random.randint(1, 10)):
    driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/textarea").send_keys(f'\n{i}')
driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/textarea").send_keys(random.random())

a = 10
while a <= 100000000000000000000000000000000000000000000000000000000000000000000000000000000:
    driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/textarea").send_keys(f'\n{a}')
    a = int(str(a) + "0")


driver.find_element(By.XPATH, "/html/body/div[2]/center[1]/form/button").click()
time.sleep(100000000000)
