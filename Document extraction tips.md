## Document Extraction Tips

This document will serve to document some lessons learned and provide tips on extracting structured text from HTML and PDF.

### Parsing HTML Documents

**Python**

I have primarily been working in Python, as it has some good, flexible capabilities, for example allowing types to be recast on the fly.  It also has a lot of libraries for accessing documents and manipulating components of documents, such as string handling and list handling.

**Beautiful Soup**

One very useful Python library for parsing and extracting data from HTML is [Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/)
Beautiful Soup is a library for Python, which provides easy canonic access to the HTML document object model by tag.  This can be very helpful in extracting structured text, by taking advantage of formatting in the document, for example titles, chapter headings, section headings and so on.

### Parsing PDF Documents

**Adobe Acrobat Professional**

I am still investigating options for parsing PDF documents into structured text.  One fortunate thing is that I have an older version of Adobe Acrobat Professional, which allows documents to be exported in various formats.  However, that doesn't necessarily solve the problems of odd formatting and extraneous tagging within the document.

