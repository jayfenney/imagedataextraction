# Extracting Data from Images of Tables

These are the methods used to extract data from tables within PDFs, including those from scanned sources. These methods use **Adobe Acrobat** and an open source program called **Tabula** to extract the data.

Fig 1.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig1.png?raw=true "Dummy Table 1")
Fig 2.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig2.png?raw=true "Dummy Table 2")

## Step 1: Get the image into readable format
No program will be able to read the numbers from your table without first putting the image through OCR software. For this I used Adobe Acrobat. Scan your table into Acrobat if required (or open the PDF if it's already in that format). In the examples (Figs. 1 & 2) above I've got two different tables that have been scanned in; table 1 has two columns of numbers very close together without any border lines, and table 2 has a column of numbers and a column of text very close. Click *Edit -> Edit Text & Images.* (Fig 3. below) This will run the document through character recognition and enable other software to read the data. *Note: If you're extracting a table from a larger document, you may want to extract specific pages from the PDF rather than putting the whole document through OCR.*

Fig 3![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig3.png?raw=true "Edit Text & Images menu option")

## Step 2: Extract the data using Tabula
Once the text has been made editable save the PDF, it'll need to be opened up in Tabula (which is available [here](https://tabula.technology)). Install Tabula and open it up, then browse to your PDF's location and click *Import*. Select your document and click *Extract Data*. You'll be presented with the pages of your document, over which you'll need to create a selection box (Fig 4.) to highlight the table or tables (this can be easier to do one page at a time depending on how clear the original source is), then click *Preview & Export Extracted Data*. On the next page you'll see what data Tabula has been able to read (Figs 5a. & 5b.), along with two options for how it reads it: if your original table contains border lines to separate rows and columns then select *Lattice*, otherwise leave it on *Stream*.

Fig 4.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig4.png?raw=true "Table opened in Tabula")
Fig 5a.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig5a.png?raw=true "Example of how data may be read by Tabula")
Fig 5b.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig5b.png?raw=true "Example of how data may be read by Tabula")

## Step 3: Clean up the extracted data
The result of the extraction process can vary greatly depending on how clear the original document is. You may find that some columns have been merged for example, or some characters may not have been recognised correctly (Fig 6). Some of the issues will be easier to fix than others.

Fig 6.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig6.png?raw=true "Example of how data may be read by Tabula")

To check columns that are supposed to only contain numbers, I'd recommended to use conditional formatting to highlight any cells that contain non-numerical characters (Fig 7.). Ones and zeros can be picked up as various other characters, and spaces can commonly be added as well. Using find and replace is an efficient way to replace these (to replace a space with nothing, highlight the column you want to fix, add a space in the find box and then press replace all, as in Fig 8.).

Fig 7.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig7.png?raw=true "Conditional formatting used to highlight numerical cells that contain non-numerical characters")
Fig 8.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig8.png?raw=true "Finding and replacing spaces")

If columns have been merged, there is no single way to fix it. If the data contained in one of the merged columns is a standard number of characters (column B in Fig 9.), it's quite a simple process to copy those characters into a new column using a combination of LEN, LEFT and RIGHT functions. If the data is more varied it may be a case of manually cutting and moving data from one column to another.  
Fig 9.![alt text](https://github.com/jayfenney/imagedataextraction/blob/master/images/fig9.png?raw=true "Finding and replacing spaces")

The final part of the clean-up process bringing the various separated comments into single cells (Fig 10.). This is done using CONCAT forumale in a separate column and bringing them all together with spaces between, using the following formula:

```=CONCAT(E2," ",F2," ",G2)```

In the example, the comments column has been split between columns E, F & G. So the formula will bring anything that's in those columns into a single column.
