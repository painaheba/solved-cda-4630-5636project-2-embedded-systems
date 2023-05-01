Download Link: https://assignmentchef.com/product/solved-cda-4630-5636project-2-embedded-systems
<br>
In this project, you need to <strong>implement both code compression and decompression using C, C++ or Java</strong>. Assume that the dictionary can have eight entries (index 3 bits) and the eight entries are selected based on frequency (the most frequent instruction should have index 000). If two entries have the same frequency, the priority should be given to the one that appears first in the original program order. The original code consists of 32-bit binaries. You are allowed to use only the following seven possible formats for compression. Note that if one entry (32-bit binary) can be compressed in more than one way, choose the most beneficial one i.e., the one that provides the shortest compressed pattern. If two formats produce exactly the same compression, choose the one that appears earlier in the following listing (e.g., <em>run-length encoding</em> appears earlier than <em>direct matching</em>). Also, if there is a scenario where you have two possible ways of applying bitmasks to a 32bit binary, always give preference to the scenario where the leftmost bit ‘1’ for the bitmask pattern (e.g., 11 is preferred over 01). Please count the starting location of a mismatch from the leftmost (MSB) bit of the pattern – the position of the leftmost bit is 00000.

Format of the Run Length Encoding (RLE)

<table width="0">

 <tbody>

  <tr>

   <td width="43">000</td>

   <td width="613">Run Length Encoding (2 bits)</td>

  </tr>

 </tbody>

</table>




Format of bitmask-based compression – starting location is counted from left/MSB

<table width="0">

 <tbody>

  <tr>

   <td width="43">001</td>

   <td width="209">Starting Location (5 bits)</td>

   <td width="228">Bitmask (4 bits)</td>

   <td width="176">Dictionary Index (3 bits)</td>

  </tr>

 </tbody>

</table>




Format of the 1 bit Mismatch – mismatch location is counted from left/MSB

<table width="0">

 <tbody>

  <tr>

   <td width="43">010</td>

   <td width="210">Mismatch Location (5 bits)</td>

   <td width="403">Dictionary Index (3 bits)</td>

  </tr>

 </tbody>

</table>




Format of the 2 bit consecutive mismatches – starting location is counted from left/MSB

<table width="0">

 <tbody>

  <tr>

   <td width="43">011</td>

   <td width="210">Starting Location (5 bits)</td>

   <td width="403">Dictionary Index (3 bits)</td>

  </tr>

 </tbody>

</table>




Format of the 2 bit mismatches anywhere – Mismatch locations (ML) are counted from left/MSB

<table width="0">

 <tbody>

  <tr>

   <td width="43">100</td>

   <td width="210">1<sup>st</sup> ML from left (5 bits)</td>

   <td width="227">2<sup>nd</sup> ML from left (5 bits)</td>

   <td width="176">Dictionary Index (3 bits)</td>

  </tr>

 </tbody>

</table>




Format of the <em>Direct Matching</em>

<table width="0">

 <tbody>

  <tr>

   <td width="43">101</td>

   <td width="211">Dictionary Index (3 bits)</td>

  </tr>

 </tbody>

</table>




Format of the <em>Original Binaries</em>

<table width="0">

 <tbody>

  <tr>

   <td width="43">110</td>

   <td width="613">Original Binary (32 bits)</td>

  </tr>

 </tbody>

</table>

<strong> </strong>

<strong>Run-Length Encoding (RLE) </strong>can be used when there is consecutive repetition of the same instruction. The first instruction of the repeated sequence will be compressed (or kept uncompressed if it is not part of the dictionary) as usual. The remaining ones will be compressed using RLE format shown above. The two bits in the RLE indicates the number of occurrences (00, 01, 10 and 11 imply 1, 2, 3 and 4 occurrences, respectively), excluding the first one. A single application of RLE can encode up to 4 instructions. Assume that the longest sequence can be at most 5 repeating instructions (the first one using other formats and the last 4 using RLE). Note that, RLE should be used when it is profitable compared to other available options.

You are expected to implement the compression and decompression functions using C, C++ or Java. You need to show a working prototype that will take any 32-bit binary (0/1 text) file and compress it to produce an output file that shows compressed patterns arranged in a sequential manner (32-bit in each line, last line padded with 1’s, if needed), a separation marker “xxxx”, followed by eight dictionary entries. Your program should also be able to accept a compressed file (in the above format) and decompress to generate the decompressed (original) patterns. Please see the sample files posted in the webpage to avoid any confusion.

<strong><u>Command Line and Input/Output Formats</u>: </strong>The simulator should be executed with the following command line. Please use parameters “1” and “2” to indicate compression, and decompression, respectively.<strong>  </strong>

<strong>./SIM</strong>  <strong>1</strong>  (or  <strong>java SIM  1</strong>)<strong>  </strong>for compression

<strong>./SIM</strong>  2  (or  <strong>java SIM  2</strong>) <strong> </strong>for decompression

Please hardcode the input and output files as follows:

<ol>

 <li>Input file for your compression function: <strong>txt   </strong></li>

 <li>Output produced by your compression function: <strong>txt</strong></li>

 <li>Input file for your decompression function: <strong>txt</strong></li>

 <li>Output produced by your decompression function: <strong>txt</strong></li>

</ol>