Download Link: https://assignmentchef.com/product/solved-cs262-assignment-2-dna-sequencing
<br>
For this assignment, you will be simulating the manipulation the nucleotides in strands of DNA.  You do not need to know much about DNA to do this assignment, but if you would like to learn more about the process, <a href="https://en.wikipedia.org/wiki/Nucleic_acid_sequence">this webpage</a> has more information.

<h4>Background</h4>

A nucleotide base is a fundamental unit that creates a genetic code found in a DNA strand (RNA will be saved for a future project). These these bases are represented by four letters which are:

<ul>

 <li>A for adenine</li>

 <li>C for cytosine</li>

 <li>G for guanine</li>

 <li>T for thymine</li>

</ul>

A chain of these nucleotide bases creates a Nucleic Acid which contains information used by living cells to construct proteins, which in turn contains the information that living organism need to survive and reproduce.  The representation of these chains can be quite long.  An example of such chains can be found <a href="https://en.wikipedia.org/wiki/Nucleic_acid_sequence#/media/File:AMY1gene.png">here</a>.  As part of genetic engineering, these chains are cut, and a sequence from another organism is inserted, or perhaps a section of the chain is excised, or removed from the larger chain.

The program you write will simulate the splicing and chains of nucleotide bases. Since there are four different letters, each letter can be represented by two bits:

<ul>

 <li>A  00</li>

 <li>C  01</li>

 <li>G  10</li>

 <li>T  11</li>

</ul>

So, for example, the nucleotide sequence GATTACA can be represented by the number sequence 2033010 (or decimal 9156 or binary 10 00 11 11 00 01 00).

You will be using bytes (unsigned char) to hold the nucleotide bases.  Each byte can hold up to four letters.  You will use bitwise operators (shifts, bitwise &amp;, |, ^, ~) to manipulate the bits in a byte to add, move, or change nucleotide letters.

<b>Specifications</b>

Your program will use the following structure to hold a nucleotide chain:

#define MAX_CHAIN_BYTES  100

typedef struct _Chain{size_t  SeqLen;  // Number of letters in sequenceunsigned char Sequence[MAX_CHAIN_BYTES];} Chain;

With this structure, a sequence can hold up to 400 different letters of a DNA sequence.  The representation (and order) of the letters will be in the smallest to largest byte in the Sequence array.  However, within a single byte, the letters will be ordered from Most Significant Bit (MSB – the leftmost bit) to Least Significant Bit (LSB – the rightmost bit).  In other words, if a sequence contains just two letters – CT, then the representation of this sequence will be found in the first byte of the Sequence array (Sequence[0]), and will have the bit pattern  0111xxxx, where the x’s can be either 0 or 1 since they will not be part of the overall sequence.  (Note: Even though the unused bits can be either 0 or 1, you may find it advantageous to set them to 0.)

You are to write a menu driven program to alter (splice, excise, or replace) sequences. The menu will contain the following options:

<ol>

 <li>Read a DNA sequence from a file</li>

 <li>Save the current sequence to a file</li>

 <li>Print the current sequence</li>

 <li>Splice and insert a sub-sequence</li>

 <li>Remove a sub-sequence</li>

 <li>Replace a sub-sequence with another sub-sequence</li>

 <li>Exit the program</li>

</ol>

User input to the menu will consist of the numbers 1-7.  Do not use any additional or different input values. Descriptions of the functionality of each input is as follows:

<ol>

 <li>When this option is selected, prompt the user to enter a filename containing a DNA sequence.  This file will be in binary format, and contain the data for a single Chain structure.  If the file can be opened successfully, the data in the file is used to initialize a variable of type Chain.  Otherwise, an error message is written to the screen, and the program returns to the main menu.  <b>Note: This option must be chosen before choosing options 2-6.  You should check that a file was successfully read before allowing options 2-6 to be executed.</b></li>

 <li>When this option is selected, prompt the user to enter a filename in which to save the data in the Chain struct containing the current sequence.  The format of the file should be the same as described for option 1 (a single Chain structure in binary format).  If the output file cannot be opened successfully, an error message is written to the screen, and the program returns to the main menu.</li>

 <li>When this option is selected, the sequence of letters is printed to the screen.</li>

 <li>When this option is selected, your program will prompt the user for two things:

  <ol>

   <li>The sub-sequence to insert – This will be a string of Nucleotide letters, and will be read from the console (not a file).  Save this input in a Chain struct variable. (Note: Use strlen() to find the length of the input string, and DON’T forget to remove the trailing ‘
’).</li>

   <li>The place to insert the sequence</li>

  </ol></li>

</ol>




<ol>

 <li value="5">When this option is selected, your program will prompt the user for a sub-sequence.  This sub-sequence will be entered from the console (not a file).  Your program will then search for the given sub-sequence throughout the entire current sequence and remove ALL instances of the given sub-sequence.  For example, if the current sequence is:</li>

</ol>

<ol>

 <li value="6">When this option is selected, your program will prompt the user for a sub-sequence to remove.  This sub-sequence will be entered from the console (not a file).  The program will then prompt the user for a sub-sequence to replace the removed sub-sequence. This sub-sequence will also be entered from the console. Note that the two sequences do not necessarily have to be the same length.  Your program will then search for the first sub-sequence throughout the entire current sequence and replace ALL instances of this sub-sequence with the second sub-sequence.  For example, if the current sequence is:</li>

</ol>

<ol>

 <li value="7">If this option is selected, print an appropriate closing message, and exit the program.</li>

</ol>

As in past assignments, part of the grading of your code will be performed by a script (sample scripts will be provided), and any additional or missing prompts will cause your program to fail to run correctly.

<b>Other Specifications and Additional Information</b>

<ul>

 <li>You must include a Makefile to compile your project.</li>

 <li>Portions of the project will be graded using a script (a sample will be provided).  It is important that your program works with any sample scripts.  Otherwise, your overall score for the project may be lowered considerably.</li>

 <li>If the size of the original sequence plus a modification is greater than the maximum length of a sequence, truncate the end of the sequence so that it is no longer than 4 * MAX_CHAIN_BYTES.</li>

 <li>For options 4, 5, and 6, if the entered sub-sequence (for replacement, removal, or insertion after) cannot be found in the current sequence, the sequence should not be modified, and an informational message (such as “sub-sequence not found”) should be printed to the screen.</li>

 <li>If an input sequence that is read from the console contains any characters other than A, C, G, or T, print an error message and re-prompt for a new sequence until a correct sequence is entered.</li>

 <li>Data in the binary files is assumed to be correct (by nature of the previous two bullets).</li>

 <li>As always, the use of global variables and variable length arrays are forbidden.</li>

 <li>All source and tarfiles should follow the standard CS262 naming conventions and contain appropriate comments.</li>

</ul>

Some Helpful Hints:

<ul>

 <li>Although the data must be read and written from/to the files in binary format, you can perform most of the other operations using cstrings.  However, you will have to convert the data from or to binary when reading or writing the files.</li>

 <li>You may find the following String Library functions useful (check man pages for proper usage):

  <ul>

   <li>strstr()</li>

   <li>strcpy()</li>

   <li>strlen()</li>

   <li>strcat()</li>

  </ul></li>

 <li>You can index within portions of a string by using the &amp; (Address-of) operator.  For example, to remove the 7th and 8th character from a string named str using strcpy, you can use the following function call:</li>

</ul>

<ul>

 <li>Strategic use of the NULL character (‘ ’) after copying sequences to temporary cstrings may help with insertion and deletion of sub-sequences.</li>

</ul>

<span class="kksr-muted">Rate this product</span>

The sub-sequence will be placed after ALL instances of the given place to insert. For example:



Your program will search for <b>all</b> instances of GGT (shown in <b>bold</b>) in the current sequence

and insert the sub-sequence (shown in lower case for this example) after each of those instances:

So, the result after this insertion will be:

Suppose the current sequence is: CATAGGTACCAGGTACA

The sequence to insert is: ACATGAThe place to insert is:  GGT

CATA<b>GGT</b>ACCA<b>GGT</b>ACA

CATA<b>GGT</b>acatagaACCA<b>GGT</b>acatagaACA

CATAGGTACATGAACCAGGTACATGAACA

Note:  If the sub-sequence happens to contain the subsequence after which to insert, it will NOT be included in the insertion (What can happen if it <b>is</b> included as the place to insert?)

CATA<b>GGTA</b>CATGAACCA<b>GGTA</b>CATGAACA

and the entered sub-sequence is:



the resulting sequence is:

GGTA

CATACATGAACCACATGAACA

CATA<b>GGTA</b>CATGAACCA<b>GGTA</b>CATGAACAthe sub-sequence to remove is:

GGTA

and the replacement sub-sequence is:



the resulting sequence is:CATA<b>AACGTGA</b>CATGAACCA<b>AACGTGA</b>CATGAACA

AACGTGA