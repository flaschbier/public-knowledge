# ZDF heute via RSS

cf. http://www.heute.de/zdfheute/rss

Wie man in Python damit umgeht, ist wohl vor allem deswegen komplex, 
weil die meisten Suchtreffer recihlich angestaubt sind.
Vielleicht mal hiermit starten:

## `feedparser`

- https://pythonhosted.org/feedparser/ – This documentation claims to describe the behavior of feedparser 5.2.0. It does not claim to describe the behavior of any other version.
- https://pypi.org/project/feedparser/ – feedparser 5.2.1
- https://github.com/kurtmckee/feedparser – letzter Commit 2 Monate alt; ein Hauptcontributor; wenige, ältere Beiträge anderer; viele offene Issues, die teils Jahre alt sind; used bei 14,7k repos; 1k stars; sieht nach einem ziemlich abgehangenen aber nur leidlich gepflegten Modul aus

Quellen
- [How to build a RSS Parser in Python? | Medium, Jan 2018](https://medium.com/@DigitallyMani/how-to-build-a-rss-parser-in-python-2879135dc2d6)
- [A Python script to read RSS feeds (and much more) | Nov. 2019](https://alvinalexander.com/python/python-script-read-rss-feeds-database/)
- [How to build a simple RSS reader in Python 3.7? | StackOverflow, Mai 2019](https://stackoverflow.com/questions/55936200/how-to-build-a-simple-rss-reader-in-python-3-7) – It seems feedparser is not compatible with python3.7 (it gives me KeyError, "object doesn't have key 'category')

### Install

```
$ conda install feedparser
Solving environment: done


==> WARNING: A newer version of conda exists. <==
  current version: 4.5.12
  latest version: 4.8.3

Please update conda by running

    $ conda update -n base -c defaults conda



## Package Plan ##

  environment location: /Users/****/anaconda3/envs/devops3

  added / updated specs: 
    - feedparser


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    feedparser-5.2.1           |           py37_1          80 KB

The following NEW packages will be INSTALLED:

    feedparser: 5.2.1-py37_1

Proceed ([y]/n)? 

Downloading and Extracting Packages
feedparser-5.2.1     | 80 KB     | ########################################################################################################################################################################################################################################### | 100% 
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
```

### Usage

`feedparser` funktioniert super für den ZDF Feed. 
Und die ARD bietet für die tagesschau auch einen an.
Damit entsteht natürlich sofort die Notwendigkeit, die zahlreichen reusebaren Teile aufzulagern.
Aber Python ist etwas ... sperrig, wenn es darum geht, leichtgewichtig was aus einem Unterverzeichnis zu reusen:
`attempted relative import beyond top-level package`

Also ein Package mit Tooling und ein paar Top-Level Skripte bauen:
- https://stackoverflow.com/questions/14132789/relative-imports-for-the-billionth-time/14132912#14132912
- https://python-packaging-tutorial.readthedocs.io/en/latest/setup_py.html (hab ich nicht hinbekommen, weil die Zielstruktur nicht gezeigt wird)
- https://python-packaging.readthedocs.io/en/latest/minimal.html# (viel besser)


## `BeautifulSoup`

- https://towardsdatascience.com/rss-feed-parser-in-python-553b1857055c – fürchterlicher Artikel, aber:

> The restriction of RSS parser libraries, basically expected me to write my own parser. Since it’s ultimately xml-based content, I decided to use the ever-reliable BeautifulSoup Library
