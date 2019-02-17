from time import sleep
from selenium import webdriver
from parsel import Selector

# Create new Instance of Chrome
driver = webdriver.Chrome('/home/praveen/anaconda3/chromedriver')

# Go to desired website
driver.get('https://offer.ebay.co.uk/ws/eBayISAPI.dll?ViewBidsLogin&item=401551356274&rt=nc&_trksid=p2047675.l2564')

# Wait 2 seconds for page to load
sleep(2)

# create Selector instance to scrape the content
sel = Selector(driver.page_source)

# Scrape the list of rows
raws = sel.xpath('//*[@class="onheadNav"]')

# list variable for storing the scraped list
sold = []

# Iterate the list and extract values in the format ['£2.99', '1', '02-Jan-19 16:44:54 GMT']
for raw in raws:
	sold.append(raw.xpath('./following-sibling::td/text()').extract())

# convert string to float nubers and find sum of numbers in the list ie. 1+1+1...
number_of_items_sold = sum(list(map(float,[i[1].replace('£','') for i in sold])))
