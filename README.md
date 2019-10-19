# Extracting Data from Images of Tables

These are the methods used to extract data from tables within PDFs, including those from scanned sources. These methods use **Adobe Acrobat** and an open source program called **Tabula** to extract the data.

1. If required, scan the table(s) into a new PDF document.
2. Open the table document into Adobe Acrobat then make the tables editable.
2.1 If the table takes up the entire document or covers multiple pages you can press *Edit* -> *Edit Text & Images* to put the whole document through preprocessing.
2.2 If the table takes up a smaller portion of the overall document, or there are multiple tables spread throughout the document, you can remove or extract pages as required before putting it through the preprocessing.
3. Once the text has been made editable save the PDF, then open it up in Tabula (available [here](https://tabula.technology))
3.1 *[Tabula opens up in a browser window, but runs entirely locally.]*
3.2 Browse to your PDF's location and then click *Import*.
3.3 Select your imported document and click *Extract Data*
3.4 You'll be presented with the pages of your document, over which you'll need to create a selection box to highlight the table or tables (this can be easier to do one page at a time depending on how clear the original source is), then click *Preview & Export Extracted Data*.
3.5 The result of this process can vary greatly depending on how clear the original document is. There is an option on the left hand side to change the extraction method to either Stream or Lattice; if the data doesn't look right, try the alternative extraction method.
3.6 The next step is to export the data into a downloadable file, which will then need to be opened and potentially cleaned up as well (the extraction process can sometimes move, remove or combine columns, rows or cells). There are various methods you might use to clean up the numerical data within the table:
3.6.1 A combination of adding 0 to a cell and conditional formatting to highlight any non-numerical cells within a column
3.6.2 Using a formula with a combination of LEFT, RIGHT and LEN commands to remove certain numbers of characters from a column of cells (particularly useful when Tabula has combined two columns together, and at least one of those columns always has the same number of characters
