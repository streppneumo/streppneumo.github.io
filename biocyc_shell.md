---
title: Using the BioCyc shell
layout: default
---

# Using the BioCyc Interactive Shell

## Starting

Open the file ```isp > biocyc > BioCyc.py```.  Run the file.  After a delay (to load the BioCyc databases), the command prompt ```>``` will appear in the terminal.

## Commands

The find command ```f``` searches all database entires and fields to a string that matches exactly.

	> f EC-2.7.1.2
	# d39
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# 19f
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# tigr4
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}

The results identify the strain (```# d39```) and the type of database object (CycCompound, CycReaction, CycGene, etc.)

To look at a database entry in detail, prefix the object's ID with ```?```.

	> ?GLC
	# d39
	CycObject: GLC
	{'CHEMICAL-FORMULA': [{'ref': None, 'attr': None, 'value': '(C 6)'},
	                      {'ref': None, 'attr': None, 'value': '(H 12)'},
	                      {'ref': None, 'attr': None, 'value': '(O 6)'}],
	 'COMMON-NAME': [{'ref': None, 'attr': None, 'value': '&beta;-D-glucose'}],
	 'CREDITS': [{'ref': None, 'attr': None, 'value': 'SRI'},
	             {'ref': None, 'attr': None, 'value': '|kaipa|'}],
	 'DBLINKS': [{'ref': None, 'attr': None, 'value': '(CHEMSPIDER "18802415" NIL |kothari| 3563632415 NIL NIL)'},
	             {'ref': None, 'attr': None, 'value': '(CAS "50-99-7" NIL |taltman| 3458663425 NIL NIL)'},
	             {'ref': None, 'attr': None, 'value': '(CHEBI "15903" NIL |taltman| 3458663425 NIL NIL)'},
	             {'ref': None, 'attr': None, 'value': '(LIGAND-CPD "C00221" NIL |taltman| 3458663425 NIL NIL)'},
	             {'ref': None, 'attr': None, 'value': '(PUBCHEM "64689" NIL |taltman| 3458663073 NIL NIL)'}],
	 'INCHI': [{'ref': None, 'attr': None, 'value': 'InChI=1S/C6H12O6/c7-1-2-3(8)4(9)5(10)6(11)12-2/h2-11H,1H2/t2-,3-,4+,5-,6-/m1/s1'}],
	 'INTERNALS-OF-GROUP': [{'ref': None, 'attr': None, 'value': '|B-DGLC-HEX-1:5|'}],
	 'MOLECULAR-WEIGHT': [{'ref': None, 'attr': None, 'value': '180.157'}],
	 'MONOISOTOPIC-MW': [{'ref': None, 'attr': None, 'value': '180.0633881178'}],
	 'NON-STANDARD-INCHI': [{'ref': None, 'attr': None, 'value': 'InChI=1S/C6H12O6/c7-1-2-3(8)4(9)5(10)6(11)12-2/h2-11H,1H2/t2-,3-,4+,5-,6-/m1/s1'}],
	 'SMILES': [{'ref': None, 'attr': None, 'value': 'C(O)C1(OC(O)C(O)C(O)C(O)1)'}],
	 'SYNONYMS': [{'ref': None, 'attr': None, 'value': 'glucose'},
	              {'ref': None, 'attr': None, 'value': 'dextrose'},
	              {'ref': None, 'attr': None, 'value': 'glc'},
	              {'ref': None, 'attr': None, 'value': 'glc-ring'},
	              {'ref': None, 'attr': None, 'value': 'D-glucose-ring'},
	              {'ref': None, 'attr': None, 'value': 'D-glucose'},
	              {'ref': None, 'attr': None, 'value': 'glucoside'},
	              {'ref': None, 'attr': None, 'value': '&beta;-D-glucopyranose'},
	              {'ref': None, 'attr': None, 'value': '&beta;-glucose'},
	              {'ref': None, 'attr': None, 'value': '6-(hydroxymethyl)tetrahydropyran-2,3,4,5-tetraol'}],
	 'TYPES': [{'ref': None, 'attr': None, 'value': 'Glucopyranose'}],
	 'UNIQUE-ID': [{'ref': None, 'attr': None, 'value': 'GLC'}]}
	# 19f
	CycObject: GLC
	{'CHEMICAL-FORMULA': [{'ref': None, 'attr': None, 'value': '(C 6)'},
	                      {'ref': None, 'attr': None, 'value': '(H 12)'},

	...snip...


Any object can be used as a query.  We can find all reactions that use glucose (GLC).

	> f GLC
	# d39
	   [CycCompound]  B-DGLC-HEX-1:5
	   [CycCompound]  GLC
	   [CycReaction]  3.2.1.33-RXN: |Truncated-Limit-Dextrins| + WATER -> CPD0-1027 + GLC   {EC-3.2.1.33}
	   [CycReaction]  TRE6PHYDRO-RXN: TREHALOSE-6P + WATER -> GLC-6-P + GLC   {EC-3.2.1.93}
	   [CycReaction]  LACTOSE6P-HYDROXY-RXN: LACTOSE-6P + WATER -> CPD-1241 + GLC   {EC-3.2.1.85}
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	   [CycReaction]  AMYLOMALT-RXN: MALTOTRIOSE + MALTOSE -> MALTOTETRAOSE + GLC   {EC-2.4.1.25}
	   [CycReaction]  ALPHAGALACTOSID-RXN: WATER + MELIBIOSE -> ALPHA-D-GALACTOSE + GLC   {EC-3.2.1.22}
	   [CycReaction]  ALDOSE-1-EPIMERASE-RXN: ALPHA-GLUCOSE <-> GLC   {EC-5.1.3.3}
	   [CycReaction]  GLUCDEHYDROG-RXN: GLC + |Ubiquinones| -> GLC-D-LACTONE + |Ubiquinols|   {EC-1.1.5.2}
	   [CycReaction]  BETAGALACTOSID-RXN: WATER + LACTOSE -> GALACTOSE + GLC   {EC-3.2.1.23}
	   [CycReaction]  KETOLACTOSE-RXN: 3-KETOLACTOSE + WATER <-?-> CPD-1242 + GLC   {EC-3.2.1.23}
	   [CycReaction]  6-PHOSPHO-BETA-GLUCOSIDASE-RXN: CPD-507 + WATER <-?-> GLC + GLC-6-P   {EC-3.2.1.86}
	# 19f
	   [CycCompound]  B-DGLC-HEX-1:5
	   [CycCompound]  GLC
	   [CycReaction]  RXN-13600: CPD-1103 + WATER -> 4-HYDROXYBENZALDEHYDE + HCN + GLC   {EC-3.2.1.21}
	   [CycReaction]  3.2.1.33-RXN: |Truncated-Limit-Dextrins| + WATER -> CPD0-1027 + GLC   {EC-3.2.1.33}
	   [CycReaction]  6-PHOSPHO-BETA-GLUCOSIDASE-RXN: CPD-507 + WATER <-?-> GLC + GLC-6-P   {EC-3.2.1.86}
	   [CycReaction]  RXN-13602: CPD-14594 + WATER <-?-> LINAMARIN + GLC   {EC-3.2.1.21}
	   [CycReaction]  RXN-13603: CPD-14596 + WATER <-?-> CPD-10277 + GLC   {EC-3.2.1.21}
	   [CycReaction]  ALDOSE-1-EPIMERASE-RXN: ALPHA-GLUCOSE <-> GLC   {EC-5.1.3.3}
	   [CycReaction]  3.2.1.21-RXN: |Beta-D-glucosides| + WATER <-?-> |Non-Glucosylated-Glucose-Acceptors| + GLC   {EC-3.2.1.21}
	   [CycReaction]  RXN-10773: CELLOBIOSE + WATER <-?-> GLC   {EC-3.2.1.21}
	   [CycReaction]  AMYLOMALT-RXN: MALTOTRIOSE + MALTOSE -> MALTOTETRAOSE + GLC   {EC-2.4.1.25}
	   [CycReaction]  ALPHAGALACTOSID-RXN: WATER + MELIBIOSE -> ALPHA-D-GALACTOSE + GLC   {EC-3.2.1.22}
	   [CycReaction]  RXN-5341: LINAMARIN + WATER <-?-> 2-HYDROXY-2-METHYLPROPANENITRILE + GLC   {EC-3.2.1.21}
	   [CycReaction]  TRE6PHYDRO-RXN: TREHALOSE-6P + WATER -> GLC-6-P + GLC   {EC-3.2.1.93}
	   [CycReaction]  BETAGALACTOSID-RXN: WATER + LACTOSE -> GALACTOSE + GLC   {EC-3.2.1.23}
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	   [CycReaction]  KETOLACTOSE-RXN: 3-KETOLACTOSE + WATER <-?-> CPD-1242 + GLC   {EC-3.2.1.23}
	   [CycReaction]  3.2.1.74-RXN: |1-4-beta-D-Glucan| <-?-> |1-4-beta-D-Glucan| + GLC   {EC-3.2.1.74}
	   [CycReaction]  LACTOSE6P-HYDROXY-RXN: LACTOSE-6P + WATER -> CPD-1241 + GLC   {EC-3.2.1.85}
	   [CycReaction]  RXN-8036: CPD-7417 + WATER <-?-> CPD-7418 + GLC   {EC-3.2.1.21}
	   [CycReaction]  RXN-9674: CPD-10277 + WATER <-?-> CPD-12699 + GLC   {EC-3.2.1.21}
	# tigr4
	   [CycCompound]  B-DGLC-HEX-1:5
	   [CycCompound]  GLC
	   [CycReaction]  3.2.1.33-RXN: |Truncated-Limit-Dextrins| + WATER -> CPD0-1027 + GLC   {EC-3.2.1.33}
	   [CycReaction]  LACTOSE6P-HYDROXY-RXN: LACTOSE-6P + WATER -> CPD-1241 + GLC   {EC-3.2.1.85}
	   [CycReaction]  ALDOSE-1-EPIMERASE-RXN: ALPHA-GLUCOSE <-> GLC   {EC-5.1.3.3}
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	   [CycReaction]  AMYLOMALT-RXN: MALTOTRIOSE + MALTOSE -> MALTOTETRAOSE + GLC   {EC-2.4.1.25}
	   [CycReaction]  ALPHAGALACTOSID-RXN: WATER + MELIBIOSE -> ALPHA-D-GALACTOSE + GLC   {EC-3.2.1.22}
	   [CycReaction]  GLUCDEHYDROG-RXN: GLC + |Ubiquinones| -> GLC-D-LACTONE + |Ubiquinols|   {EC-1.1.5.2}
	   [CycReaction]  BETAGALACTOSID-RXN: WATER + LACTOSE -> GALACTOSE + GLC   {EC-3.2.1.23}
	   [CycReaction]  KETOLACTOSE-RXN: 3-KETOLACTOSE + WATER <-?-> CPD-1242 + GLC   {EC-3.2.1.23}
	   [CycReaction]  6-PHOSPHO-BETA-GLUCOSIDASE-RXN: CPD-507 + WATER <-?-> GLC + GLC-6-P   {EC-3.2.1.86}
	   [CycReaction]  MALTODEG-RXN: MALTOHEXAOSE + MALTOSE <-?-> CPD0-1133 + GLC


To limit our search to reactions where glucose is a reactant, we can perform a specific find with the ```ff``` command.  A specific find command takes a string and a field name.  Only results containing a match in the field will be returned.  Since reactants are listed in the reaction's ```LEFT``` field, we can find glucose consuming reactions as follows.

	> ff GLC LEFT
	# d39
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	   [CycReaction]  GLUCDEHYDROG-RXN: GLC + |Ubiquinones| -> GLC-D-LACTONE + |Ubiquinols|   {EC-1.1.5.2}
	# 19f
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# tigr4
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	   [CycReaction]  GLUCDEHYDROG-RXN: GLC + |Ubiquinones| -> GLC-D-LACTONE + |Ubiquinols|   {EC-1.1.5.2}

We can find reactions matching and EC number 2.7.1.2 number with ```ff EC-2.7.1.2 EC-NUMBER```.  Note that BioCyc stores EC numbers with the 'EC-' prefix.  The ```e``` command is a shortcut for finding reactions by EC number.

	> ff EC-2.7.1.2 EC-NUMBER
	# d39
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# 19f
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# tigr4
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	> e 2.7.1.2
	# d39
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# 19f
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# tigr4
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}

Only queries with the ```e``` command do not require the 'EC-' prefix on the EC number.

The ```x``` command exits the interactive shell.

## Complex Queries

The ```q``` command runs a complex query against the database.  A complex query is assembled by combining two commands, matching (```m```) and getting (```g```).

The matching command takes the form ```string m name```.  The command returns all objects in the database containing a field *name* with a value matching *string*.  The matching command is similar to the ```ff``` command.

	> q GLUCOKIN-RXN m UNIQUE-ID
	# d39
	   [str]  GLUCOKIN-RXN ?UNIQUE-ID -> GLUCOKIN-RXN: GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# 19f
	   [str]  GLUCOKIN-RXN ?UNIQUE-ID -> GLUCOKIN-RXN: GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# tigr4
	   [str]  GLUCOKIN-RXN ?UNIQUE-ID -> GLUCOKIN-RXN: GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	> ff GLUCOKIN-RXN UNIQUE-ID
	# d39
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# 19f
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}
	# tigr4
	   [CycReaction]  GLUCOKIN-RXN: GLC + ATP -> PROTON + GLC-6-P + ADP   {EC-2.7.1.2}

The ```m``` command matches a field and returns a list of objects, while the get command ```g``` returns the value of a specific field.  To lookup the reaction direction on each glucokinase reaction, we can apply the ```g``` command on the results of a matching command.

	> q GLUCOKIN-RXN m UNIQUE-ID g REACTION-DIRECTION
	# d39
	   [str]  GLUCOKIN-RXN ?UNIQUE-ID -> GLUCOKIN-RXN .REACTION-DIRECTION -> LEFT-TO-RIGHT: LEFT-TO-RIGHT
	# 19f
	   [str]  GLUCOKIN-RXN ?UNIQUE-ID -> GLUCOKIN-RXN .REACTION-DIRECTION -> LEFT-TO-RIGHT: LEFT-TO-RIGHT
	# tigr4
	   [str]  GLUCOKIN-RXN ?UNIQUE-ID -> GLUCOKIN-RXN .REACTION-DIRECTION -> LEFT-TO-RIGHT: LEFT-TO-RIGHT

Although each query must begin with a string and a ```m``` command, the ```m``` and ```g``` commands can be compined in alternating fashion to assemble arbitrarily complex queries.  Below is a command to identify genes associated with a reaction name by tracing through the enzyme links.

	> q GLUCOKIN-RXN m REACTION g ENZYME m PRODUCT g ACCESSION-1
	# d39
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNIX6-478 .ENZYME -> GIX6-580-MONOMER ?PRODUCT -> GIX6-580 .ACCESSION-1 -> SPD_0580: SPD_0580
	# 19f
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNI07-702 .ENZYME -> GI07-1575-MONOMER ?PRODUCT -> GI07-1575 .ACCESSION-1 -> SPT_1614: SPT_1614
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNI07-411 .ENZYME -> GI07-683-MONOMER ?PRODUCT -> GI07-683 .ACCESSION-1 -> SPT_0692: SPT_0692
	# tigr4
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNHGN-696 .ENZYME -> GHGN-669-MONOMER ?PRODUCT -> GHGN-669 .ACCESSION-1 -> SP_0668: SP_0668

## Macros

Complex commands like the gene association lookup shown above can be arduous to type.  *Macros* allow queries to be named and saved for quick recall.  A macro call take the form ```.name string```, where *name* is the macro name and *string* is the string that starts the query (the first argument after the ```q``` command).  The ```.``` in front of the macro name identifies the command as a macro.

The gene association-finding query above is stored as a macro named ```gpr``` (for gene-protein-reaction relationship).  The previous query can be abbreviated as

	> .gpr GLUCOKIN-RXN
	# d39
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNIX6-478 .ENZYME -> GIX6-580-MONOMER ?PRODUCT -> GIX6-580 .ACCESSION-1 -> SPD_0580: SPD_0580
	# 19f
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNI07-702 .ENZYME -> GI07-1575-MONOMER ?PRODUCT -> GI07-1575 .ACCESSION-1 -> SPT_1614: SPT_1614
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNI07-411 .ENZYME -> GI07-683-MONOMER ?PRODUCT -> GI07-683 .ACCESSION-1 -> SPT_0692: SPT_0692
	# tigr4
	   [str]  GLUCOKIN-RXN ?REACTION -> ENZRXNHGN-696 .ENZYME -> GHGN-669-MONOMER ?PRODUCT -> GHGN-669 .ACCESSION-1 -> SP_0668: SP_0668

