# GTF/GFF Files

**GTF (Gene Transfer Files)** or **GFF (General Feature Files)** store annotation information about a particular sequence.

- Features can be: genes, exons, introns, primer binding sites, origins of replications, anything you can think of.
- GTF/GFF files are made of tab-separated columns. Each row is a “feature”.
- GTF/GFF files can be paired with a FASTA file to give a user the complete information about a sequence and all its features.
- GTF files can be uploaded to visual viewers of genomes and the features can be graphically displayed.
- File extensions can be .gff, gff2, gff3, or gtf. These share much of the same formatting with the exception of the the way the group information is formatted.
- The tab-separated columns of information are:

| # | Feature | Description |
| --- | --- | --- |
| 1 | seqname | The name of the sequence. Must be a chromosome or scaffold |
| 2 | source | The program that generated this feature |
| 3 | feature | The name of this type of feature. Some examples of standard feature types are “CDS”, “start codon”, “stop codon”, and “exon”. |
| 4 | start | The starting position of the feature in the sequence. The first base is numbered 1. |
| 5 | end | The ending position of the feature (inclusive). |
| 6 | score | A score between 0 and 1000. If the track line useScore attribute is set to 1 for this annotation data set, the score value will determine the level of gray in which this feature is displayed (higher numbers = darker gray). If there is no score value, enter “:.”:. |
| 7 | strand | Valid entries include “+”, “-”, or “.” (for don't know/don't care). |
| 8 | frame | If the feature is a coding exon, frame should be a number between 0-2 that represents the reading frame of the first base. If the feature is not a coding exon, the value should be “.”. |
| 9 | group | All lines with the same group are linked together into a single item. |

EXAMPLE:

```
$ more saccharomyces_cerevisiae_R64-1-1_20110208.gff 
chrI    SGD     chromosome      1       230218  .       .       .       ID=chrI;dbxref=NCBI:NC_001133;Name=chrI
chrI    SGD     repeat_region   1       62      .       -       .       ID=TEL01L-TR;Name=TEL01L-TR;Note=Terminal%20stretch%20of%20telomeric%20repeats%20on%20the%20left%20arm%20of%20Chromosome%20I;dbxref=SGD:S000028864
chrI    SGD     telomere        1       801     .       -       .       ID=TEL01L;Name=TEL01L;Note=Telomeric%20region%20on%20the%20left%20arm%20of%20Chromosome%20I%3B%20composed%20of%20an%20X%20element%20core%20sequence%2C%20X%20element%20combinatorial%20repeats%2C%20and%20a%20short%20terminal%20stretch%20of%20telomeric%20repeats;dbxref=SGD:S000028862
chrI    SGD     repeat_region   63      336     .       -       .       ID=TEL01L-XR;Name=TEL01L-XR;Note=Telomeric%20X%20element%20combinatorial%20Repeat%20region%20on%20the%20left%20arm%20of%20Chromosome%20I%3B%20contains%20repeats%20of%20the%20D%2C%20C%2C%20B%20and%20A%20types%2C%20as%20well%20as%20Tbf1p%20binding%20sites%3B%20formerly%20called%20SubTelomeric%20Repeats;dbxref=SGD:S000028866
chrI    SGD     gene    335     649     .       +       .       ID=YAL069W;Name=YAL069W;Ontology_term=GO:0003674,GO:0005575,GO:0008150;Note=Dubious%20open%20reading%20frame%20unlikely%20to%20encode%20a%20protein%2C%20based%20on%20available%20experimental%20and%20comparative%20sequence%20data;dbxref=SGD:S000002143;orf_classification=Dubious
chrI    SGD     CDS     335     649     .       +       0       Parent=YAL069W;Name=YAL069W;Ontology_term=GO:0003674,GO:0005575,GO:0008150;Note=Dubious%20open%20reading%20frame%20unlikely%20to%20encode%20a%20protein%2C%20based%20on%20available%20experimental%20and%20comparative%20sequence%20data;dbxref=SGD:S000002143;orf_classification=Dubious
```

Figure: An example of a genome sequence (.fa) and annotation file (.gtf) that are rendered as browsable pictures on the [UCSC Genome Browser](https://genome.ucsc.edu/cgi-bin/hgTracks?db=ce11&lastVirtModeType=default&lastVirtModeExtraState=&virtModeType=default&virtMode=0&nonVirtPosition=&position=chrII%3A14631486%2D14645321&hgsid=2909126220_ONoxCiAHmYllJx8EXJGctuCOGa6F)

<p align="center">
<img width="410" alt="browser shot" src="https://github.com/jesshill/CSU-2025FA-DSCI-510-001_LINUX_as_a_computational_platform/blob/main/Images/browser_shot.png">
</p>

Back to [File Formats](../Modules/Week2/2-4_File_Formats.md)

Back to [Practice grep and cut](../Modules/Week2/2-7_Practice_grep_and_cut.md)
