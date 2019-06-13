### Extracted Features Readme

Last updated June 13, 2019

This project and code is the result of an initiative by Temple's Digital Scholarship Center to create a method for creating and sharing extracted features (that is, non-consumable versions) of copyrighted work for research purposes. 

### Contents

The Text_Disag_project folder contains a few elements:

1) this README file

2) sample (subsection) output data, in bags_of_words and matrix_output

3) R_script, which contains the R code for this project

### Requirements

1) The code is only compatible with Mac operating systems at this time; sorry if you are using a PC! 

2) Your raw data files must be UTF-8 encoded text (.txt) files, placed in the text_data folder

3) You set three initial parameters within the code itself. These are explained at more length in in-code comments.  They are:  
     1) The text delimiter (a string) (preset to "CHAPTER")
     2) If you would like to create subsections from your section (boolean) (preset to TRUE)
     3) The subsection size - # of words (integer) (preset to 100, this value is ignored if subsection is set to FALSE)


### Using the code

1) Follow the instructions above

2) Ensure correct placement and encoding of your project folder and raw text data

3) Delete old results from bags_of_words and matrix_output folder (to avoid mixing of old and new outputs)

4) Highlight and run the entire code in R Studio.  Outputs are generated and placed automatically
   in the appropriate folders. If these folders do not exist, they will be created for you.


### This code is useful for:

1) __*Sectioning texts*__

It is useful for many research purposes, such as topic modeling, to break texts into smaller pieces.  These methods often works more reliably, and give more accurate results, when applied to many smaller parts of a long text, rather than a few long but complete texts.

This code can separate one or more long text(s) into smaller pieces, based on a single shared section indicator, or delimiter, shared between all of the texts (for example, sectioning books into chapters for chapter-level analysis). It then gives output both of each section as a separate bag-of-words text file (with words re-ordered alphabetically), and also with each section title and section contents in a single .csv file.

Note: if zero instances of the delimiter are present in a text, this code will return the entire contents of that text as one single document.

2) __*Sub-sectioning the delimited texts*__

Some texts do not have regular delimiters, making sectioning on a delimiter impractical or impossible.  In other instances, long texts may only have a few instances of regular delimiters, resulting in sections that are still longer than desired.  Text data mining methods like topic modeling also work most reliably on sections of text that are roughly the same length - and book chapter length (for example) varies widely between books, and often even within one book.  Sub-sectioning standardizes document length for methods sensitive to this text attribute.

If the 'use_subchapter' argument in the beginning of this code is set to TRUE, the code will instead perform two steps of analysis.  First, it will section texts based on the common delimiter (exactly as above).  

Then, the code will separate longer chapters into subsections of equal length, based on the value of the 'subch_threshold' argument.  Word order is maintained at this point, to ensure that each subsection captures the first, second, third... through nth part of each section.  Short sections/chapters will be kept intact.

Finally, as above, the word order is re-sorted from the order present in the text to alphabetic.

3) __*Transforming text data into subsectioned "Bags of Words" texts and spreadsheets*__

The functional forms of many text data analysis modeling methods (in particular, methods that work from a term-document-frequency matrix) ignore word order.  Also, while it is illegal to share copyrighted material in its consumable (that is, human-readable) form, it IS legal to share the 'extracted features' of these texts.  Word counts, presented as a term-document-frequency matrix or as disaggregated (disordered) word tokens (aka "bags of words"), qualify as one of these extracted features.  Therefore, the output of this code can be shared freely for research purposes in instances where the original texts themselves could not be.  This code is ideal for collaborative projects focused on analysis of copyrighted text for text data mining / cultural analytics purposes.
