<!-- 
.. title: Using Scrapy to Extract Scientific Names from PestNet Fact Sheets
.. slug: using-scrapy-to-extract-scientific-names-from-pestnet-fact-sheets
.. date: 2017-05-18 13:00:26 UTC+10:00
.. tags: scrapy, python
.. category: 
.. link: 
.. description: 
.. type: text
-->

PestNet serves a couple of hundred excellent pest fact sheets on its site at http://www.pestnet.org/fact_sheets/index.htm. Unfortunately, these are indexed only by vernacular names. I want to hyperlink to sheets using scientific names.  So I wrote a  [scrapy](https://scrapy.org/) script to crawl the site and scrape the section from each page which contains scientific names.  

~~~python
from scrapy.spiders import CrawlSpider, Rule
from scrapy.contrib.linkextractors import LinkExtractor
import re

class someSpider(CrawlSpider):
    name = 'crawltest'
    allowed_domains = ['www.pestnet.org']
    start_urls = ['http://www.pestnet.org/fact_sheets/index.htm']
    rules = ( Rule(LinkExtractor(allow=()), follow=True, callback='parse_item'), )


    # Let's capture scientific names
    def parse_item(self, response):
        log = 'scientific_names_log.md'
        s = str(response.body)
        searchObj = re.search( r'<a name="Scientific Name"(.*?)<a name=', s, re.M|re.I)
        if searchObj:
            result = searchObj.group(1)
        else:
            result = "Nothing found!!"
        with open(log, 'a') as f:
            f.write('{} {}\n'.format(response.url, result))
        return
~~~

The script was invoked from the terminal using:
~~~sh
scrapy runspider scrapePP.py -s DEPTH_LIMIT=1
~~~

Here are the first few lines from **scientific_names_log.md**:
~~~md
http://www.pestnet.org/fact_sheets/mini/index.htm Nothing found!!
http://www.pestnet.org/fact_sheets/batiki_blue_grass_eye_spot_207.htm ></a><h1 class="" style="False">Scientific Name</h1><P><EM>Curvularia ischaemi</EM></P>
http://www.pestnet.org/fact_sheets/bean_pod_borer_037.htm ></a><h1 class="" style="False">Scientific Name</h1><P><EM>Maruca</EM> <EM>vitrata</EM>; it used to be known as <EM>Maruca testulalis.</EM></P>
http://www.pestnet.org/fact_sheets/bean_lace_bug_253.htm ></a><h1 class="" style="False">Scientific Name</h1><P><EM></EM>&nbsp;<EM>Corythucha gossypii</EM></P>
http://www.pestnet.org/fact_sheets/bean_phaseolus_rust_217.htm ></a><h1 class="" style="False">Scientific Name</h1><P><EM>Uromyces appendiculatus</EM> \r\nvar. <EM>appendiculatus.</EM> Previously <EM>Uromyces \r\nphaseoli.</EM> </P>
~~~

As you can see, there was still some work to be done to clean this up. I used the [atom](https://atom.io/)  editor to delete the extraneous bits and saved urls and scientific names to 
[pacific_pests_insects.csv](https://aubreymoore.github.io/blog/pacific_pests_insects.csv). Note that this file contains info only on arthropod pests.
