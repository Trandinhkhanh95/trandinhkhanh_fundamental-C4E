from urllib.request import urlopen
from bs4 import BeautifulSoup
import pyexcel
from collections import OrderedDict

url = "https://www.apple.com/itunes/charts/songs/"
#1 Open connection
conn = urlopen(url)
#2 Download raw data
raw_data = conn.read()
#3 Decode raw data
webpage_text = raw_data.decode("utf-8")

soup = BeautifulSoup(webpage_text,"html.parser")
section = soup.find("section","section chart-grid")
li_list = section.find_all("li")
li = li_list[0]

new_list = []
for li in li_list:
    a = li.h4.a
    artist = a.string
    b = li.h3.a
    name = b.string
    link = url + a["href"]
    news = {
        "Artist" : artist,
        "Name" : name,
        "Link":link,
    }
    new_list.append(news)
print(*new_list,sep="\n")
pyexcel.save_as(records= new_list, dest_file_name="artis&song.xlsx")

