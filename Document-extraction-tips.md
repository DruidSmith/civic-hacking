## Document Extraction Tips

This document will serve to document some lessons learned and provide tips on extracting structured text from HTML and PDF.

**General Info**

This document will talk about various tools and types of documents, as I wrestle through the challenge and teach myself tricks for extracting documents.  As I dig deeper, I will be talking about a variety of things, like programming languages (i.e. Python) as well as some software tools.

Not yet explored, but showing promise:

- [Apache Tika](http://tika.apache.org/) - recommended by [Sophia Parafina](http://twitter.com/spara)
- [Apache PDFBox](http://pdfbox.apache.org/) - recommended by [Steve Citron-Pousty](http://twitter.com/@TheSteve0) - appears to be geared toward extracting data from PDFs.
- [Data Science Toolkit](http://www.datasciencetoolkit.org/) - recommended by [Harry Wood](http://twitter.com/harry_wood)
- [CAM-PDF](http://search.cpan.org/~cdolan/CAM-PDF-1.60/lib/CAM/PDF.pm) - recommended by [Jeremiah Felt](http://twitter.com/jeremiahfelt)

### Parsing HTML Documents

**Python**

I have primarily been working in Python, as it has some good, flexible capabilities, for example allowing types to be recast on the fly.  It also has a lot of libraries for accessing documents and manipulating components of documents, such as string handling and list handling.

**Beautiful Soup**

One very useful Python library for parsing and extracting data from HTML is [Beautiful Soup](http://www.crummy.com/software/BeautifulSoup/)
Beautiful Soup is a library for Python, which provides easy canonic access to the HTML document object model by tag.  This can be very helpful in extracting structured text, by taking advantage of formatting in the document, for example titles, chapter headings, section headings and so on.

### Parsing PDF Documents

**Tabula:  For PDF Containing Tables**

From [Joe Larson](https://twitter.com/oeon), this tip: use [Tabula](http://source.mozillaopennews.org/en-US/articles/introducing-tabula/) from Mozilla Open.  It allows you to upload a PDF containing tabular data, and returns a csv.

**Adobe Acrobat Professional**

I am still investigating options for parsing PDF documents into structured text.  One fortunate thing is that I have an older version of Adobe Acrobat Professional, which allows documents to be exported in various formats.  However, that doesn't necessarily solve the problems of odd formatting and extraneous tagging within the document.

One thing that was useful was processing the PDF in Acrobat to optimize and reduce size.  That appears to have consolidated some of the tagging.  Given a document of nearly 2,000 pages, I still had some issues of Adobe crashing while attempting to export the document.  To that end, I split it into two smaller pieces using the Adobe Acrobat "extract pages" function, which perhaps also may leave behind any other embedded oddities in the document that many have been leading to crashes.

## How to Publish The Opened Documents

### Statutory and Regulatory Documents

For this civic hacking challenge, I have been dealing primarily with trying to open statutory and regulatory documents, in this case municipal codes.  I have been using the XML format provided by the [Open Government Foundation "State Decoded" project](Open Government Foundation "State Decoded" project)