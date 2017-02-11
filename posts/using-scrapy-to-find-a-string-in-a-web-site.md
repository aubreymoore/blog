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

I wanted to find pages on the University of Guam College of Natural and Life Sciences Web Site containing a specific string. This short python script, which uses the [scrapy](https://scrapy.org/) framework, does the trick:

~~~python
from scrapy.spiders import CrawlSpider, Rule, LinkExtractor

class someSpider(CrawlSpider):
  name = 'crawltest'
  allowed_domains = ['cnas-re.uog.edu']
  start_urls = ['http://cnas-re.uog.edu']

  rules = (
     Rule(LinkExtractor(allow=()), follow=True, callback='parse_item'),
  )

  def parse_item(self, response):
    target = 'bell pepper'
    if target in str(response.body):
      print(response.body[0:100])
      print('>>>>>>>>>> ', target, ' found in ', response.url)
~~~

Executed from the command line using:

~~~sh
scrapy runspider test_spider.py -s DEPTH_LIMIT=2 &> output.txt
~~~

