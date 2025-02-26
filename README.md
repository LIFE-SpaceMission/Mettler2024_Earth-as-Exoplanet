# Earth as an Exoplanet. III. Using Empirical Thermal Emission Spectra as an Input for Atmospheric Retrieval of an Earth-twin Exoplanet

Real disk-integrated spectra and ground truths for observations of different Earth views with the AIRS and IASI instruments. These spectra were used as input for the retrievals in Earth as an Exoplanet III (Mettler et al. 2024; ApJ 963:24 (25pp)).

Link to the paper: https://iopscience.iop.org/article/10.3847/1538-4357/ad198b

All spectra assume the Earth to orbit a G2V star (Sun-like) on a circular 1AU orbit at a distance of 10pc from the observer. The exozodiacal dust emission is assumed to be three times the level of the local zodiacal light.




## Description of the different subdirectories:


- `Spectra_AIRS/`
	Contains the 24 different AIRS spectra (2 files per spectrum) used in the grid retrievals (Section 3 in publication).
	
- `Spectra_IASI/` 
	Contains the 16 different IASI spectra used for the comparison in Figure 2.

- `Ground_Truths/`
	Contains the ground truth abundance profiles and the P-T structures used compare the retrieval results to.




## Structure of the filenames in the `Spectra_AIRS/` and `Spectra_IASI/` subdirectories:
	
	
``` 
R<Resolution>_<View>_LIFEsim_SN<S/N>_<Instrument>.txt
```

- **Resolution:** Resolution of the spectrum. Values: `50`, `100`.
- **View**: Earth view and season of the spectrum. Values: `NP17JAN`, `NP17JUL`, `SP17JAN`, `SP17JUL`, `EqC17JAN`, `EqC17JUL` (see publication for details on the name scheme).
- **S/N**: S/N of the spectrum in the 11.2 micron bin. Values: `10`, `20`.
- **Instrument**: Specifies the used instrument. Values:
	- `long`: long wavelength data from the AIRS instrument.
	- `short`: short wavelength data from the AIRS instrument.
	- `IASI`: data from the IASI instrument.



## Structure of the files in the `Spectra_AIRS/` and `Spectra_IASI/` subdirectories:

Each file contains the following 3 columns:  
  
  
``` 
	First Column      Second Column         Third Column           
	Wavelengths      Flux at 10 pc       Noise on Flux at 10 pc  
	[micron]       [erg s-1 Hz-1 m-2]     [erg s-1 Hz-1 m-2]

```


## Structure of the filenames in the `Ground_Truths/` subdirectory:
	

```
	<Parameter>_profiles_limb_adj/<Parameter>_profile_limb_adj_<View>.txt
```


- **Parameter**: Ground truth parameter name. Values: `CH4`, `CO`, `H2O`, `O3`, `P-T`.
- **View**: Earth view and season of the Ground truth. Values: `NP17_Jan`, `NP17_Jul`, `SP17_Jan`, `SP17_Jul`, `EqC17_Jan`, `EqC17_Jul`(see publication for details on the name scheme).

The CO2 ground truths are stored in the file: "`GroundTruths_CO2_diskavg_limb_adj.txt`".
For CO2 an iso-profile is assumed throughout the atmosphere. This file contains a dictionary (data for all Views) an can be opened in Python as follows:

```
file = open(truth_dir+'/GroundTruths_CO2_diskavg_limb_adj.txt', 'rb')
dataCO2 = pkl.load(file)
file.close()
```



## Structure of the files in the `Ground_Truths/<Case>/` subdirectories:

Each file contains the following 3 columns:

```
First Column		Second Column		   Third Column

Pressure		Ground truth value	     Ground truth uncertainty
[hPa]			P-T data: [K]		     P-T data: [K]
			Abundance data: [MMR]	     Abundance data: [MMR]
```

