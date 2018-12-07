# -*- coding:utf-8 -*-
import urllib
import urllib2
import re
import requests
import os
import time
import random

for page in range(700,800):
#page = 33
	print page
	time.sleep(2);
	#http://the_website/thread-4558665-1-1.html
	#url = 'http://the_website/forum-18-' + str(page) + '.html'
	url = 'http://the_website/thread-4558' + str(page) + '-1-1.html'
	user_agent2 = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:63.0) Gecko/20100101 Firefox/63.0'
	user_agent = 'Mozilla/'+random.randint(1,9)+'.0 (compatible; MSIE 5.5; Windows NT)'
	cookie = 'Cookie: can be down by burp or in save in your own server'
	headers = { 'User-Agent' : user_agent, 'Cookie' : cookie}
	try:
		request = requests.get(url,headers = headers)
		#response = urllib2.urlopen(request)
		#content = request('utf-8')
		#pattern = re.compile('<a href=".*?class="xst">(.*?)</a>',re.S)
#<a href="javascript:;"><img id="aimg_13442515" aid="13442515" src="static/image/common/none.gif" onclick="zoom(this, this.getAttribute('zoomfile'), 0, 0, '0')" zoomfile="data/attachment/forum/201707/27/021745lso6pia8if4rxiaq.jpg" file="data/attachment/forum/201707/27/021745lso6pia8if4rxiaq.jpg.thumb.jpg" alt="1507081617ec58a66a66ade524.jpg" title="1507081617ec58a66a66ade524.jpg" w="534"></a>
		pattern = re.compile('zoomfile="data/attachment/forum/(.*?)"\sfile="data/attachment/forum/.*?"\salt="(.*?)"\stitle="',re.S)
		items = re.findall(pattern,request.text)
		for item in items:
			#haveImg = re.search("img",item[3])
			#if not haveImg:
			#	print item[0],item[1],item[2],item[4]
			print item[0]
			typename = item[0].split('.')[1]
			#print typename
			urlforimg = 'http://the_website/data/attachment/forum/' + item[0]
			headers = {'User-Agent': 'Mozilla/7.0 (Windows NT 6.1; WOW64; rv:55.0) Gecko/20100101 Firefox/53.0'}
			req = urllib2.Request(url=urlforimg,headers=headers)
			res = urllib2.urlopen(req)
			local = os.path.join('/home/bp_down/bipi_big/',item[1])
			try:
				urllib.urlretrieve(urlforimg, local)
			except IOError:
				pass
			continue

	except urllib2.URLError, e:
		if hasattr(e,"code"):
			#print e.code
			pass
		if hasattr(e,"reason"):
			#print e.reason
			pass
