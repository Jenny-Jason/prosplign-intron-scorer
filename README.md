# ProSplign intron scorer

Tomas Bruna, Alexandre Lomsadze, Mark Borodovsky

Georgia Institute of Technology, Atlanta, Georgia, USA

Reference: _GeneMark-EP and -EP+: automatic eukaryotic gene prediction supported by spliced aligned proteins_ (paper in preparation, 2019)

## Description

ProSplign boundary scorer parses introns from ProSplign's alignment output and
scores them. Introns are scored based on local alignment quality around their
boundaries. Detailed description of how the scores are computed is available
in (TODO: add link to manuscript)

## Installation and usage

To install, clone this repository and run `make` in the root folder.

To run, use the following command:

    prosplign_intron_scorer -i input_file -o output_file [-w integer] [-am] [-s matrix_file] [-k kernel]

The program can parse multiple separate alignments saved in the same input.

Available options are:

```
   -i Path to input file.
   -o Where to save output file.
   -w Width of a scoring window around introns.
   -a Print all introns. Without  this flag, only  introns
      with canonical splite sites and perfectly scored in-
      trons with GC-AG and AT-AC splice sites are printed.
   -m Multiply partial scores from the left and right boun-
      daries of the intron. Default behavior is to sum the 
      scores from both sides.
   -s Use specified scoring matrix for intron scoring. Wi-
      thout this option, amino acid scores are determined 
      based on the quality indicator in the input alignment 
      file.
   -k Specify type of weighting kernel used. Available opti-
      ons are "triangular", "linear", "parabolic" and 
      "triweight". Triangular kernel is the default option.
```

## Tests

Unit tests are located in the `test` folder. To compile a test binary, run
`make test` in the root folder. Subsequently, run the test binary to evaluate
the tests:

    make test
    test/t_prosplign_intron_scorer
