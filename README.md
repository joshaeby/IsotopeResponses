# IsotopeResponses
Data characterizing stable isotopes in Earth, and the response functions for scattering with dark matter. Ancillary data for arXiv: aaaa.bbbbb

There are two files, both in .dat format:

1. **Isotope_Data.dat** contains information characterizing the distribution of nuclear isotopes in the bulk of the Earth.
	
 	We include only elements which are either (1) stable or (2) have decay lifetime longer than the age of the Earth.
	
 	The lightest isotope is hydrogen (Z=1, A=1) and the heaviest is lead (Z=82, A=208).
	
 	For each isotope, the file lists:
	- the **element symbol** (one or two letters) specifying the identity of the atom (e.g. helium is He, carbon is C).
	- the **atomic number** Z (e.g. helium has Z=2, carbon has Z=6)
	- the **mass number** A of the specific isotope (e.g. helium has A=3 or A=4, carbon has A=12 or A=13)
	- the **spin** (integer or half-integer) and **parity** (+ or -) of the isotope (e.g. 4He has 0+, 13C has 1/2-)
	- the **isotopic fraction** (between 0 and 1) of a given element which is found in the specified isotope (e.g. 0.9893 of all carbon in the Earth is in the form of 12C).
		Note that the isotopic fractions, summed over all isotopes for a given element, should equal unity.
		Note that the entries are rounded to four decimal places, so a value of 0 in the table implies an isotopic fraction less than 10^{-5}.
	- the **magnetic moment** of each isotope, measured in units of the Bohr magneton _e/(2*mp)_ with _mp_ the proton rest mass and _e_ the elementary charge.
		In SI units, _e/(2*mp) = 5.05078*10^{-27} Joule/Tesla_ .
	- the *number density* of each _element_ in Earth's core in units of _km^{-3}_
	- the *number density* of each _element_ in Earth's mantle in units of _km^{-3}_
	- the *number density* of each _element_ in Earth's crust in units of _km^{-3}_
		The number density of a given isotope can be estimated by multiplying the number density of an element by the relevant isotopic fraction.


2. **Nuclear_Response_Data.dat** contains the coefficients of the polynomial characterizing dark-matter--nucleus scattering through a variety of non-relativistic operators.
	 These are calcluated using the nuclear shell code **BigStick**, available online at https://github.com/cwjsdsu/BigstickPublick, see https://arxiv.org/abs/1801.08432 for information.

	- The isotopes included are: 12C, 14N, 24Mg, 25Mg, 27Al, 28Si, 29Si, 30Si, 54Fe, 56Fe, 57Fe, 58Fe, 60Fe, 70Ge, 72Ge, 73Ge, 74Ge, 87Sr, 88Sr. These are labeled by their atomic and mass numbers (_Z,A_).

	- The operators included are: M, Σ'' (Sigmapp), Σ' (Sigmap), Φ'' (Phipp), \tilde{Φ}' (Phitildep), Δ (Delta), MΦ'' (MPhipp), Σ'Δ (SigmapDelta).

	- For each isotope and each operator, we specify the isospin combinations (τ,τ')=(00,01,10,11).
	 For example, the entry beginning with _WSigmapp10    	 12	 25			..._ is the response function for 25Mg scattering through the Σ'' operator with (τ,τ')=(1,0).

	- The remaining entries are the coefficients ηi of the polynomial characterizing the response function, which take the form

   		W_A^{ττ'} = e^{-2y}(η + η1*y + η2*y^2 + η3*y^3 + η4*y^4 + η5*y^5 + η6*y^6 + η7*y^7 + η8*y^8)

   	 	We truncate the expansion (arbitrarily) at eighth order.

	 Note that due to limitations of the **BigStick** codebase and nuclear physics uncertainty, we expect errors to be sub-percent for light elements, _Z<20_, and approaching _10-50%_ for elements as heavy as iron (and heavier).
