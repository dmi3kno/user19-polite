From the early days, we teach our kids to behave decent around the table to not grab food with their fingers. Yet, we somehow forget to tell the newcomers to the data community about the responsible web scraping practices. 

Today I want to talk to you about 4 of them. Here they are on the screen.

***

First: “Talk to your Junior Data Scientists about the user-agent string, before somebody else does”. In the dark streets of the web, they learn how to mislead the host to believe they are operating a popular web browser, or even several of them. Teach them to be proud about using R and never hesitate to declare it to the world.

Here’s an example of a sneaky, dishonest and intentionally misleading user-agent, and another one which is perhaps more straightforward, allowing the host to contact the user and clarify any possible question or concerns.

***

Second principle is related to permissions. “Knock before you enter”. Robots.txt is a special file usually found in the root folder of the website, regulating who gets to scrape where how fast and how often. There’s this old Roman saying: “What is allowed to Internet Explorer is not necessarily allowed to Beautiful Soup”. It is within the user responsibility to investigate what permissions apply to them. 

I advise everyone to develop a habit of preceding the scraping function with an `if` statement, checking the path is in fact scrapeable. And in case of the google search page, it is NOT.

***

Next principle is related to the speed at which the data is acquired. This is the area where we should be proud that “R is slooow”. I have seen geniuses setting up sophisticated parallelization to make R scrape faster. On the contrary,  you should attempt to make R run slower, using “ratelimiter” or a new adverb in the purrr family, called “slowly”.

Don’t just lapply the scraper function. Instead, use rate limiting to make sure you never overwhelm the host. I think it is fair to say that if you’re getting an error message, which you need to google to understand, you’re doing something wrong.

***

Finally, it a good idea to cache everything you get from the server. Don’t live in a fear of accidentally terminating the webscraping session. Instead, check out the memoise package, which allows you to cache the function calls to memory or to disk. It is liberating to be certain that you just can restart your R session and pick up where you left off.

Memoise is an adverb. It makes the function “remember” all previous calls together with respective arguments, so that if you make the same call again, results will retrieved from the cache, not the  server. Alternatively, you can serialize any R object to an RDS file and then retrieve it from there.

***

Today, I want to present you an R package called `polite`. It contains two main functions: “bow and scrape”, which implement these principles. The first one introduces you to the host and checks robots.txt for you. Should you ever need to change the path on the same server, you can simply `nod` to it and carry on on your business. Scrape, on the other hand, is a wrapper over httr::GET and it performs rate-limiting and memoisation. There’s also a helpful downloader called `rip()`.

“bow and scrape” do not only mean performing a traditional medieval greeting gesture, but also figuratively mean being polite, considerate and generally act as a grown-up.

***

Bob Rudis is one the vocal proponents of an online etiquette in the R community. If you have never seen his robots.txt file, you should definitely check it out! Lets look at his blog. We don't know how many pages will the gallery return, so we keep going until there’s no more “Older posts” button. 

Note that I first bow to the host and then simply `nod` to the current scraping page inside the while loop. We organize the data into the tidy format and append it to our empty data frame. At the end we will discover that Bob has written over 560 blog articles, which I very much recommend anyone to check out.

***

The most recent addition to `polite` package is a usethis-like function to produce example script you can include in your own package. The only dependencies in the templated code are httr, robotstxt and memoise. Just type polite::use_manners and implement your own webscraper that adheres to polite philosophy. 

***

I want to leave you with this ethical webscraper manifesto and the link to the slides. 

And remember, the most polite behavior is to avoid scraping at all. Investigate if the host has an official API and use that instead. The objective should never be to simply hoard the data, but to create insight and value in a polite and respectful manner.
