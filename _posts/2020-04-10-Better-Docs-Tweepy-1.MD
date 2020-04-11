---
layout: post
title:  "Better Docs Part 1: Tweepy Error Handling"
date:   2020-04-10 23:13:00
categories: Better Docs
---
# Better Docs Part 1
Opensource software is incredibly important for modern programmers. The software is important and yet it often is only maintained by a few core developers. One of the problems of this is that documentation isn't always maintained that well which can lead to countless hours spent learning the nuances of libraries that could have been spent on the problem itself. This series will serve to highlight some of things I come across while dealing with different libraries. 

### Tweepy Error Handling
The python Tweepy module is a useful for library for sending requests to Twitter's search API. For those gathering significant amount of tweets, handling rate limits properly is important for streamlining continuos crawling. One of the problems with the Tweepy module is that errors are handled in the TweepyError class. Accessing error codes from these TweepyError instances isn't outlined clearly in the Tweepy documentation. The tweepy API class also provides some error handling, however this requires enumerating all of the codes you wish to accept. Using a limiter wrapper around a cursor object I do the following:

``` Python
def limiter_tweepy_error_handler(cursor)
        while 1:
            try:
                yield cursor.next()
            except tw.TweepError as e:
                errors_list = eval(e.response.text)
                errors_list = errors_list['errors']
                codes = set()
                for error in errors_list:
                    codes.add(error["code"])
                if 429 in codes or 88 in codes:
                    print('Rate Limit Error Waiting 15 mins')
                    time.sleep(15*60)
```

The error message can be accessed as a dictionary through the ```response``` attribute of the TweepError. I used the code above to specifically wait for 15 mins based on two separate error codes. This could obviously be extended to handle a variety of issues while you mitigate the limitations Twitter puts on this free service.
