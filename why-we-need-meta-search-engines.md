# What is a Meta Search Engine and Why do we even need it?

Search engines are an integral part of the Internet. Could you imagine the Internet without Google search?

The Internet has billions and billions of websites with loads of content but it's the search engines that make them discoverable.

So is there any difference between search engines and meta search engines? What exactly is a meta search engine?

---

A metasearch engine, otherwise known as an aggregator, is a search engine that sends queries to several search engines and either aggregates the results into one master list or categorizes the results by the search engines they come from.


**Believe it or not, they’ve been around for a long time.**

### Then, What Is a Meta Search Engine?

Metasearch engines work by sending requests made by a user in the search slot of a metasearch engine to numerous other search engines. The servers of the metasearch engine wait for answers from the requested search engines before they can show the final results. The results are presented based on certain guidelines depending on how they are adjusted.

![Meta Search Engine Working](/images/metasearchworking.jpg)


---

### Pro's of Meta Search Engine

1. Customisable on how to get results from other search engines
2. More Privacy compared to other normal search engine
3. No profiling of the searches to serve ads across the web


---

There are many meta-search engines out in the market, but in this blog we are going to know more `Searxng Meta Search Engine`.

SearXNG is a free internet metasearch engine which aggregates results from various search services and databases. Users are neither tracked nor profiled.

![Searxng Search Console Pic](/images/searxng.png)

---

### How does SearXNG protect privacy?

SearXNG protects the privacy of its users in multiple ways regardless of the type of the instance (private, public). Removal of private data from search requests comes in three forms:

1. removal of private data from requests going to search services
2. not forwarding anything from a third party services through search services (e.g. advertisement)
3. removal of private data from requests going to the result pages

Removing private data means not sending cookies to external search engines and generating a random browser profile for every request. Thus, it does not matter if a public or private instance handles the request, because it is anonymized in both cases. IP addresses will be the IP of the instance. But SearXNG can be configured to use proxy or Tor. Result proxy is supported, too.

SearXNG does not serve ads or tracking content unlike most search services. So private data is not forwarded to third parties who might monetize it. Besides protecting users from search services, both referring page and search query are hidden from visited result pages.

---

#### Why use a private instance?

  *"Is it worth to run my own instance?"*

\.\. is a common question among SearXNG users.  Before answering this question,
see what options a SearXNG user has.

Public instances are open to everyone who has access to its URL.  Usually, these
are operated by unknown parties (from the users' point of view).  Private
instances can be used by a select group of people.  It is for example a SearXNG of
group of friends or a company which can be accessed through VPN.  Also it can be
single user one which runs on the user's laptop.

### How to Install Seaxng using Docker

https://gist.github.com/sidmulajkar/9a313e34fe2e79f15f58fb4ca81264eb

---

### How to use Searxng in a hackable without using docker

https://gist.github.com/sidmulajkar/f3877b905251d4fee6f1ac323145cf89
