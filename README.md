#This is the beginning of my AutoApply Application/API/BOT


# The purpose of this application is to gather information from a user. Have an ETL scrape a Job board for matching positions, and to have a resume retrieved from storage and sent to the job posting.

##Step 1 will be to identify a bot or method to collect the following information. (Name, email, password, keywords for job search)
#investigate which containers I can use for the front end of the app. Investigate Dockers and Container to find a solution


##Step 2 will be to develop an ETL that pulls the job information from the job board and runs a filter to remove duplicates and a refined search for keywords.

This link shows how to use python and the library beautiful soup to scrape websites for code.
https://realpython.com/beautiful-soup-web-scraper-python/

#Beautiful soup code
import requests
from bs4 import BeautifulSoup


URL = "https://realpython.github.io/fake-jobs/"
page = requests.get(URL)

soup = BeautifulSoup(page.content, "html.parser")
results = soup.find(id="ResultsContainer")

# Look for Python jobs
print("PYTHON JOBS\n==============================\n")
python_jobs = results.find_all(
    "h2", string=lambda text: "python" in text.lower()
)
python_job_elements = [
    h2_element.parent.parent.parent for h2_element in python_jobs
]

for job_element in python_job_elements:
    title_element = job_element.find("h2", class_="title")
    company_element = job_element.find("h3", class_="company")
    location_element = job_element.find("p", class_="location")
    print(title_element.text.strip())
    print(company_element.text.strip())
    print(location_element.text.strip())
    link_url = job_element.find_all("a")[1]["href"]
    print(f"Apply here: {link_url}\n")
    print()
################################################################################################################################################################
####### this is how u comment

#leave white space all the time

##Step will be storing the information in a variable and writing a script to pull your resume from storage and email it to the variable.

cant believe I put all this in a mark down file.

I need to organize this folder

# chop wood, carry water

every day I'm hustling
