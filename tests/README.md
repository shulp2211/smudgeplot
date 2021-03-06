### Manual tests

This is a place for manual tests that have not been automated (yet?).
Don't forget to re-install the package/script before execution. Somehting like

```
Rscript install.R
install -C exec/smudgeplot /usr/local/bin
install -C exec/smudgeplot_plot.R /usr/local/bin
```

should do the job.

#### interface tests

##### smudgeplot plot

```
./exec/smudgeplot plot tests/data/toy_middle_coverages.tsv -o tests/data/toy_middle_R -n 100 -nbins 20
```

generates a smudgeplot from the toy data.

##### smudgeplot hetkmers

two different methods to extract homologous kmers

###### All

```
./exec/smudgeplot hetkmers -o tests/data/toy_all tests/data/toy_kmer_k21.dump
```

###### Middle

```
./exec/smudgeplot hetkmers -o tests/data/toy_middle tests/data/toy_kmer_k21.dump --middle
```

generates two files `tests/data/toy_middle_coverages.tsv` and `tests/data/toy_middle_sequences.tsv` with coverages and sequences of kmer pairs.


##### smudgeplot kmer extraction

```
exec/smudgeplot.py extract -cov tests/data/toy_all_coverages.tsv -seq tests/data/toy_all_sequences.tsv   -minc 400 -maxc 410 -minr 0.49 -maxr 0.5 | head
```

would extract 80 lines made of 20 kmers pairs, but showing only the first ten.