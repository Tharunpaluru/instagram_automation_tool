from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import time

# Create a new instance of the Firefox driver
driver = webdriver.Firefox()

# Navigate to Instagram's login page
driver.get("https://www.instagram.com/accounts/login/")

# Wait for the page to load
time.sleep(2)

# Find the username and password fields and enter your credentials
username_input = driver.find_element_by_name("username")
username_input.send_keys("YourUsername")
password_input = driver.find_element_by_name("password")
password_input.send_keys("YourPassword")

# Press the enter key to log in
password_input.send_keys(Keys.ENTER)

# Wait for the page to load after logging in
time.sleep(3)

# Search for a specific hashtag or user
search_input = driver.find_element_by_xpath('//input[@placeholder="Search"]')
search_input.send_keys("YourHashtagOrUsername")
time.sleep(2)
search_input.send_keys(Keys.ENTER)

# Wait for the search results to load
time.sleep(2)

# Click on the first result
first_result = driver.find_element_by_class_name("yCE8d")
first_result.click()

# Wait for the user's profile to load
time.sleep(2)

# Like the user's first 3 posts
for _ in range(3):
    like_button = driver.find_element_by_class_name("fr66n")
    like_button.click()
    time.sleep(1)
    next_button = driver.find_element_by_class_name("coreSpriteRightPaginationArrow")
    next_button.click()
    time.sleep(2)

# Follow the user
follow_button = driver.find_element_by_xpath('//button[text()="Follow"]')
follow_button.click()

# Close the browser
driver.quit()
