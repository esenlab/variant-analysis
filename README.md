# variant-analysis
Tools to examine and analyze population genomic data

Protocol: Generation of a Figure Comparing Genomic Variant Types to Fractional Solvent Accessible Surface Area (SASA)
*Objective:* This protocol aims to generate a figure that compares the count of genomic variant types at a specific amino acid sequence position in a gene to the degree of its occlusion form surface water in the structure. Fractional SASA is used as an indicator of how deeply an amino acid is embedded in the structure. The produced figure shows a direct correlation between an increased fractional SASA and the number of variant types at a specific position.
*Materials Required:*
1. Variant data CSV file from the Broad Institute Genome Aggregation Database (gnomAD). Use the 'Export variants to csv' option.
2. Solvent Accessible Surface Area (SASA) text file or CSV from PyMol. To acquire this, use the command: get_sasa_relative [ selection [, state [, vis [, var [, quiet [, outfile [, subsele ]]]]]]].
3. Shift variable from UniProt. This is essential since the variant data from gnomAD is human-based while the SASA data from PyMol may be derived from a different organism (e.g., rat, ground squirrel). The shift variable adjusts for this difference by changing the position number in humans to align with the SASA data position numbering. The script will request a value for the shift variable during execution.
4. MATLAB platform.

*Procedure:*
1. Download the MATLAB script and open it.
2. Download the gnomAD variant data CSV.
3. Generate a text file of fractional SASA values for the region of interest in PyMOL.
   - Visit RCSB.org to identify an appropriate structure for your gene. Note down the 4-digit code for the structure.
   - Launch PyMOL, navigate to File → Get PDB, enter the 4-digit code in the PDB ID box, and download the chosen structure.
   - Select the region of interest. For instance, 'select subunit, /7lp9/A/A/111-360' selects the region of structure 7lp9 from amino acid position 111 through 360 and designates the selection as 'subunit'.
   - Generate a txt file of SASA values for the region. For instance, for the selection named 'subunit', use the command 'get_sasa_relative subunit, outfile = fileName.txt'.
4. Ensure that all data files are stored in the same directory as the MATLAB script.
5. If the PDB structure used for SASA value generation is non-human, visit UniProt and align the sequences for your gene to determine the shift variable.
6. Finally, execute the MATLAB script.

*Caution:* Please be aware that the gnomAD variant data CSV includes variants from the noncanonical transcript. These variants are indicated in the browser window with daggers next to the HVGS consequence but are not present in the downloaded CSV.
