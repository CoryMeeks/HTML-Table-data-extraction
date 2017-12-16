# HTML-Table-data-extraction
This is a TopCoder project: Unstructured text mining is the key the future of data science.  Many data sources provide valuable data in unstructured and semi-structured formats.  Frequently, tables in HTML are messy, and complex to find within large bodies of text.  Headers change, can be misaligned, numbers can be in different formats.   The tables titles are frequently labeled outside the table structure. Mastering the extraction of this information in a generic way can provide a very powerful tool for understanding many different forms of data.   Our goal in this project is to build a tool that takes an html file as input and as the output produces structured text in JSON format with data from the tables in the document. For example, given a table in this image
<img src="http://pokit.org/get/img/9bc0d326b25306d5fe5376bb417dfd9e.jpg" >

The tool would produce output like this one

[{

"Assets": "Current assets.Cash and cash equivalents",

"July 1, 2017": 18571,

"September 24, 2016": 20484

},

{
"Assets": "Current assets.Short-term marketable securities",
"July 1, 2017": 58188,

"September 24, 2016": 46671

},

{

"Assets": "Current assets.Accounts receivables, less...",

"July 1, 2017": 12399,

"September 24, 2016": 15754

},

{

"Assets": "Current assets.Inventories",

"July 1, 2017": 3146,

"September 24, 2016": 2132

},

{

"Assets": "Current assets.Vendor non...",

"July 1, 2017": 10233,

"September 24, 2016": 13545

},

{

"Assets": "Current assets.Other current assets",

"July 1, 2017": 10388,

"September 24, 2016": 8283

},

{

"Assets": "Current assets.Other current assets.Total current assets",

"July 1, 2017": 112875,

"September 24, 2016": 106869

}]
 

Specifically, the tool should extract every number in the table labeled by:
The row name including sub-row names aligned to the tree (ie "Current assets.Inventories" in the above example - dot concatenated string)
The column header including any information for multiple headers (ie "Assets", "July 1, 2017",.. in the above example). In case of multiple headers, like here the column name can also be dot concatenated string
The units for the number e.g. dollars, shares (you can infer this from either cell value, header value or text before/after the table)
The date associated with the number from the header (ie normalize date values where possible ->"July 1,2017" and "September 24, 2016" should be normalized to common format)
The value in absolute units  - eg 1 million should be 1000000
No commas or other separators in values
All HTML tags must be stripped from the output
Any additional information about the cell value that can be inferred, such as if it is a pro forma number or not
The output should also contain meta data about the table and the document
The name of the table from any headers above the table or outside table
The date of the document from the index
The company name / ID associated with the table
The originating document type if there is a type
Scope of this challenge is building the complete table data extraction tool. It will be a command line tool that accepts HTML file (or HTML string) as a parameter, extracts the data and outputs it to a json file. Recently we ran an ideation challenge to get some ideas for data extraction and the winning submissions are available in the forums. You should check them out and reuse the ideas outlined there (or ignore them completely), but we encourage you to explore other options. Review will be based on the ideation scorecard and the submission with best performance/best features wins. For example a great idea would be rendering the html document in a headless browser (phantomJS, Chrome) to get visual information about sub-row names, multispan columns, etc.
For testing/verification we will use the 10-K and 10-KA documents from SEC, available at EDGAR Database - you can do a search for a company name (Facebook, Apple, Microsoft,..) and then filter out 10-K and 10-KA documents.
Implementation must be in Python, Java or Scala. Any libraries must be Apache, BSD or MIT licensed. GPL is not permitted.
