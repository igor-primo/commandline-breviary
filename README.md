# brev: commandline-breviary

I modified the [Divinum-Officium](https://github.com/DivinumOfficium/divinum-officium) script for generating EPUB files in order 
to show the office or mass propers in plain text format, serving as a command-line
program.

The perl script that calculates the office of the day generates the office content
in Xhtml format. I use 'html2text' to extract the contents and 'sed' to format it
a little bit. This may cause some overhead, specially when generating several files.
While I learn perl scripting this will be the way to go. One may view the files 
in Xhtml as well.

Generating Mass Propers and generating Offices are mutually exclusive operations.
If one wishes to do both, he/she will have to generate one after the other.

## usage

`brev -o <HOUR>`

This command generates of office <HOUR> of current day and pipes the content 
into 'less' pager. <HOUR> Can be: Matutinum, Laudes, Tertia, Sexta, Nona, Vespera, Completorium.

`brev -o <HOUR> -x`

This command generates the office <HOUR> of current day leaving it as a Xhtml 
files and pipes it into lynx.

`brev -m`

Generates the Mass Propers for the current day and pipes the Xhtml contents
into 'less' pager.

`brev -m -x`

Generates the Mass Propers for the current day and pipes it into lynx.
This is a buggy option for the time being.

`brev -w`

Generates all Office files of all months of the current year and writes
them into files with names 'breviarium-$MONTH.txt'. A file for all Offices
of the year is created. This last file is just the appending of all
month files in order.

`brev -w -m`

The same as the previous one, but the contents are the Mass Propers.

The other options are similar to the original script.

`brev -o <HOUR> -r <RUBRICS>`

This command generates the Office <HOUR> using the <RUBRICS> rubric.
<RUBRICS> can be 1570, 1910, DA, 1955, 1960, Newcal, Dominican,
Monastic. A similar command is provided for Mass Propers: 
`brev -m -r <RUBRICS>`. In both cases, the default rubric is 
1960.

`brev -o <HOUR> -v`

Generates the Office <HOUR> using the Parvum Blessed Virgin Mary
votive office.

`brev -p -o <HOUR>`

Generates the Office <HOUR> with statements suitable to a priest.
For example, 'Domine, exaudi orationem meam' is substituted for
'Dominus vobiscum'.

`brev -y <FIRST_YEAR> -t <LAST_YEAR> -w [-m]`

Generates all the files specified as in '-w' but with the first year
<FIRST_YEAR> and last year <LAST_YEAR>.

`brev -o <HOUR> -d MONTH-DAY-YEAR`

Generates the hour of the specified date. The -d can also be combined
with -m. If the date is invalid, brev will print the office/mass
of the current day.

## installation

You can place the project directory in some digital attic of your
preference and modify the CDUR brev script veriable to the directory
of brev script. You can simply execute the 'cdur' script and it will
do this for you. Also, place the to brev into the PATH environment
variable.

## dependencies

So far as I know it requires the basic perl modules set that is required
by a simple GNU/Linux installation. I leave my installed modules at
the time of writing this for reference if desired.

## TODO

* To use multiprocessing to make generation of text files faster.

## similar programs

[Vulgate](https://github.com/LukeSmithxyz/vul)

[King James Version](https://github.com/LukeSmithxyz/kjv)

[Septuagint and more](https://github.com/LukeSmithxyz/grb)

## notes

Thanks for the [Divinum-Officium](https://github.com/DivinumOfficium/divinum-officium)
project for the dedication they put into preserving the spiritual oasis that once glorified
the Church of Rome.
