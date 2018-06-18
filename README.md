# Circos-Py
## B-Cell Clones as Circos Plots

This script was made to illustrate the expansion of B-cell clones over multiple timepoints by converting a spreadsheet input to a [Circos](http://circos.ca/) plot.  In this specific case, the orange and blue colors depict specific B-cell phenotypes.

![example_input_data](example.png)

With the circos-py repository installed and setup, the above plot can be generated by navigating to the `circos-py` directory at the command line and running the `make_circos_plots.py` script with the example input data as shown below.

```shell
cd ~/circos-py
python make_circos_plots.py example_input_data.csv
```

## Install
### Quick-Guide
Just a quick gerneral guide for Mac users: if you do not actively use Python, Perl, or Circos already I would recommend installing [Anaconda3](https://www.anaconda.com/download/), then installing Perl via conda:

```
conda install -c anaconda perl
```

Then install [Circos](http://circos.ca/software/download/), unzip, and symlink to usr/local/bin:

```
cd ~/Desktop
wget http://circos.ca/distribution/circos-0.69-6.tgz
tar xvfz circos-0.69-6.tgz
ln -s ~/Desktop/circos-0.69-6/bin/circos /usr/local/bin/circos
```

You should now be able to run circos from the command line.  Check this by running the following from the terminal:

`$ circos -v`

And you should see something similar to:

`circos | v 0.69-6 | 31 July 2017 | Perl 5.022000`

Now it's time to check what Perl modules are needed to run Circos: `circos -module`

A list of modules should sputter forth.  Use the below snippet to install all Circos Perl modules with CPAN:

```
cpan Carp Clone Config::General Cwd Data::Dumper Digest::MD5 File::Basename File::Spec::Functions File::Temp FindBin Font::TTF::Font GD GF::Polyline Getopt::Long IO::File List::MoreUtils List::Util Math::Bezier Math::BigFloat Math::Round Math::VecStat Memoize POSIX Params::Validate Pod::Usage Readonly Regexp::Common SVG Set::IntSpan Statistics::Basic Storable Sys::Hostname Text::Balanced Text::Format Time::HiRes
```

Last thing is to clone this repository:

```
git clone git@github.com:greenkidneybean/circos-py.git
```

### Circos
Unfortunately Circos takes a bit of effort to get up and running.  If you're on a Mac I'd recommend [installing via Homebrew](http://circos.ca/tutorials/lessons/configuration/distribution_and_installation/).  
### Circos-Py


## Setup
### Add Circos Binary to Your Shell Path

### Changes in the Circos Defaults

I've included my Circos configuration files which use fonts that are not included in the Circos Plot package.  Circos supports true type (.ttf) and open type (.otf) fonts, which can be added to the Circos package (fonts/modern/). To use an added font you must add a key term to the Circos fonts file (etc/fonts.conf) and the path to the font.  For example:  

`arial_bold = fonts/modern/Arial Bold.ttf`  

I'm also delimiting all my data files (karyotype and links) with tabs instead of spaces (the default).  This can be changed in housekeeping.conf file (etc/housekeeping.conf).

`file_delim = \t`

## Input File Requirements
- Input file must be an Excel workbook (.xlsx)
  - Each sample must have its own sheet
  - The sheet name will be used as a label for all data generated from that sheet
- Each sheet requires the following 4 columns
  - `timepoint` - identifies the timepoint from which the sequence was derived
  - `clone` -  used to assign the sequence to a clone group
  - `seq_id` - unique identifier for the sequence
  - `spec` - phenotypic or subpopulation information
## Output Circos Plots

**ToDo:**
- Add two more sample to example data
- create circos module with all functions
- Lock package dependencies
- Web GUI
