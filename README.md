# weird-autocg-thing
Dear Shahriar,

Basically this is a fork of the auto-cgui github where I had to change some things to make it do what we want. It should run by pip installing the relevant modules, and then just playing around with things in maker.ipynb

Here are the necessary modules:

selenium
splinter
pyyaml
biopython

You will also need chrome.

Here is a description of the relecant files:

maker.ipynb - this is the file where our functions are defined. it's a bit of a mess right now, but make_pdb creates a pdb of the complex we are interested in with glycans attached at every possible n-glycosylation site. these sites are found by searching for Asn - X - Ser/Thr. the input is the pdb_code and a list of glycans.
grs_sampler.txt - this is a file where our glycan library will be stored. 
tarz/ - folder where the tar files are stored after make_pdb(...) executes

Here is an explanatory code sample:

code = '1tb6'
grs = sample_grs('grs_sampler.txt') # gets a random grs
glycans = put_n_everywhere(code, grs) # generates an object which stores an instance of our chosen glycan at every available n glycosylation site
print(glycans)
make_pdb(code, glycans, mod_name = 'solution') # mod_name = 'solution' generates solvated pdb, but mod_name = 'pdb' can be used to generate unsolvated pdb and is much faster.
