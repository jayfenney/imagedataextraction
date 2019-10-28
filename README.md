# Extracting Data from Images of Tables

These are the methods used to extract data from tables within PDFs, including those from scanned sources. These methods use **Adobe Acrobat** and an open source program called **Tabula** to extract the data.

Fig 1![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig1.png?raw=true "Dummy Table 1")
Fig 2![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig2.png?raw=true "Dummy Table 2")

## Step 1: Get the image into readable format
No program will be able to read the numbers from your table without first putting the image through OCR software. For this I used Adobe Acrobat. Scan your table into Acrobat if required (or open the PDF if it's already in that format). In the examples above I've got two different tables that have been scanned in; table 1 has two columns of numbers very close together without any border lines, and table 2 has a column of numbers and a column of text very close. Click *Edit -> Edit Text & Images.* (Fig 3 below) This will run the document through character recognition and enable other software to read the data. *Note: If you're extracting a table from a larger document, you may want to extract specific pages from the PDF rather than putting the whole document through OCR.*

Fig 3![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig3.png?raw=true "Edit Text & Images menu option")

## Step 2: Extract the data using Tabula
Once the text has been made editable save the PDF, then open it up in Tabula, which is available [here](https://tabula.technology)). Install Tabula and open it up (it runs via a web browser, but it's run from a local location). Browse to your PDF's location and then click *Import*. Select your document and click *Extract Data*. You'll be presented with the pages of your document, over which you'll need to create a selection box to highlight the table or tables (this can be easier to do one page at a time depending on how clear the original source is), then click *Preview & Export Extracted Data*. On the next page you'll see what data Tabula has been able to read, along with two options for how it reads it: if your original table contains border lines to separate rows and columns then select *Lattice*, other leave it on *Stream*.

Fig 4![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig4.png?raw=true "Table 1 opened in Tabula")
Fig 5![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig5.png?raw=true "Table 1 opened in Tabula")

## Step 3: Clean up the extracted data
The result of the extraction process can vary greatly depending on how clear the original document is. You may find that some columns have been merged for example, or some characters may not have been recognised correctly. Some of the issues will be easier to fix than others.  

If columns have been merged, there is no single easy way to fix it. If the data contained in one of the merged columns is a standard number of characters, it's quite a simple process to copy those characters into a new column using a combination of LEN, LEFT and RIGHT functions. If the data is more varied it may be a case of manually cutting and moving data from one column to another.  

To check columns that are supposed to only contain numbers, it's recommended to use conditional formatting to highlight any cells that contain non-numerical characters. Ones and zeros can be picked up as various other characters, using find and replace is an efficient way to replace these, along with extra spaces that may get added as well.
