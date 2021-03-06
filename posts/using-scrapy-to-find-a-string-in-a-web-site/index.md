<!-- 
.. title: Using Scrapy to Find a String in a Web Site
.. slug: using-scrapy-to-find-a-string-in-a-web-site
.. date: 2017-02-11 19:57:33 UTC+10:00
.. tags: python scrapy
.. category: 
.. link: 
.. description: 
.. type: text
-->

Last updated Sunday, 12. February 2017 07:53AM 

I wanted to find pages on the University of Guam College of Natural and Life Sciences Web Site containing a specific string. This short python script, which uses the [scrapy](https://scrapy.org/) framework, does the trick:

### test_spider.py
~~~python
from scrapy.spiders import CrawlSpider, Rule
from scrapy.contrib.linkextractors import LinkExtractor

class someSpider(CrawlSpider):
  name = 'crawltest'
  allowed_domains = ['cnas-re.uog.edu']
  start_urls = ['http://cnas-re.uog.edu']
  rules = ( Rule(LinkExtractor(allow=()), follow=True,callback='parse_item'), )
  
  def parse_item(self, response):
    target = 'bell pepper'
    log = 'test_spider_log.md'
    if target in str(response.body):
      with open(log, 'a') as f:
        f.write('**{} was found in <{}>\n'.format(target, response.url))
    return
~~~

### Executed from the command line using:
~~~sh
scrapy runspider test_spider.py -s DEPTH_LIMIT=2
~~~

### Output: test_spider_log.md
**bell pepper** was found in <http://cnas-re.uog.edu/soils-of-guam/>

**bell pepper** was found in <http://cnas-re.uog.edu/cnas-publications/?auth=&limit=17&tgid=&type=&usr=&yr=>

**bell pepper** was found in <http://cnas-re.uog.edu/cnas-publications/?auth=&tgid=115&type=&usr=&yr=>

**bell pepper** was found in <http://cnas-re.uog.edu/cnas-publications/?auth=&tgid=66&type=&usr=&yr=>


___
