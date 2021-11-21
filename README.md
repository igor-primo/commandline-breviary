# brev: commandline-breviary

	I modified the Divinum-Officium script for generating EPUB files in order 
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
	into 'less' pager.
	
	<HOUR> can be: Matutinum, Laudes, Tertia, Sexta, Nona, Vespera, Completorium.

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

## installation

	i.,
