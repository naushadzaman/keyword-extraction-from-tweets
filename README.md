# keyword-extraction-from-tweets
keyword extraction from tweets using python 
In this module, we use Pattern tools to do POS tagging/Phrase extraction of tweets. The usual POS tagging/chunking tools do not work well for free form texts like tweets, so we needed to use a tool that is designed and trained for twitter/tweets. From Pattern tool output, we extract phrases as entities. You can decide to use on NP (Noun Phrase), but our default is to use NP (Noun Phrase) and ADJP (Adjective Phrase). With this tool, you can also extract hashtags, usernames, urls from the tweet. 

Questions, comments, feedbacks: n@uzzaman.com, @naushadzaman.


# Install requirements (Pattern)
Pattern: http://www.clips.ua.ac.be/pattern
$ pip install -r requirements.txt

# Examples
$ python 

## Sample keyword extraction
>>> import keyword_extraction_w_parser
>>> query = "The mobile web is more important than mobile apps."
>>> keyword_extraction_w_parser.get_keywords(query)
[u'mobile web', u'mobile apps', u'important']

If we want to extract only the NP (Noun Phrase). 
>>> keyword_extraction_w_parser.get_keywords(query, ['NP'])
[u'mobile web', u'mobile apps']

Another example: 
>>> query = "As a #roadmapscholar, I highly recommend #startup bootcamp for #founders by @andrewsroadmaps : http://t.co/ZBISIMEBRH http://t.co/VF5CojRWNF"
>>> keyword_extraction_w_parser.get_keywords(query)
[u'roadmapscholar', u'startup bootcamp', u'founders']

## Sample extraction of other entities 
For tweets, hashtags, usernames, urls are obvious entities that we might need to extract. We provide that functionality as well. 

Extract hashtags:
>>> query = "As a #roadmapscholar, I highly recommend #startup bootcamp for #founders by @andrewsroadmaps : http://t.co/ZBISIMEBRH http://t.co/VF5CojRWNF"
>>> keyword_extraction_w_parser.extract_hashtag(query) 
['#roadmapscholar', '#startup', '#founders']

Extract usernames (twitter handles): 
>>> query = "RT @andrewsroadmaps: Proud of @naushadzaman &amp; @WasimKhal for winning the #IBMWatson hackathon! #roadmapscholars https://t.co/08sbAjKWKu"
>>> keyword_extraction_w_parser.extract_users(query)
['@andrewsroadmaps', '@naushadzaman', '@wasimkhal']

Extract urls/links: 
>>> query = "As a #roadmapscholar, I highly recommend #startup bootcamp for #founders by @andrewsroadmaps : http://t.co/ZBISIMEBRH http://t.co/VF5CojRWNF"
>>> keyword_extraction_w_parser.extract_link(query)
['http://t.co/ZBISIMEBRH', 'http://t.co/VF5CojRWNF']


