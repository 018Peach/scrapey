# scrapey
Developed a Python web scraper using Selenium to extract information about phones from the Smartprix website, which I intend to use for an app I am developing using FlutterFlow for a college project.

Here are the steps involved to develop this scraper:

1. Import all the necessary modules.
2. Create a new instance of the Chrome WebDriver. Chrome is the recommended choice for Selenium automation.
3. Install your preferred extension from the following website: [Extension cbx install](https://standaloneinstaller.com/online-tools/crx-downloader). Visit the Chrome Web Store, find the desired extension, copy its URL, and use the provided website to download the .crx extension file. Save the file in the same folder as your code.
4. Navigate to the Smartprix. I have chosen to scrape links for smartphones that are currently in stock, excluding upcoming phones. Additionally, the phones are sorted from high to low price to facilitate targeted data extraction.
5. Upon visiting the website, I determine the total number of phones to be scraped and store this number in a variable. I use a loop to scrape all the phones.
6. The website displays only 20 phones at a time. After scraping these phones, I need to click the "Load More" button to load the next set of phones for scraping. To automate this process, I check the value of the variable "i" mod 20. If "i" is less than 20, the load button is not clicked. If "i" is between 20 and 40, the load button is clicked once, and so on.
7. For each set of 20 phones, I visit them one by one by incrementing the specified XPath in the code. I extract the phone's href (link), visited this href link and then extracted phone's name, price, image, and buy links. In case of any exceptions, these values are set to "None".
8. Next, I click on the "View More Specs" button to access additional detailed information about the phone, such as chipset, dimensions, and 5G bands. Clicking the button opens a popup containing a table. To scrape this table, I follow these steps:
    - Within the "content" tag, I search for the table and visit each table in a loop.
    - Similar to the previous step, I increment the XPath to visit each row in the table and extract the key-value pairs.
    - If any exceptions occur during this process, the specs data is set to "None".
9. The extracted data is then appended to an Excel file. I check if a file named "product.xlsx" already exists. If it does, I open it; otherwise, I create a new file.
10. The first row of the Excel file contains the attribute names (e.g., phone name, price, SIM size, battery size, display type), while the subsequent rows store the corresponding data for each phone (e.g., Samsung S23, ₹70,000, nano SIM, 4000mAh, OLED 120Hz, etc.).
11. After appending the data for each phone, the Excel file is saved.
