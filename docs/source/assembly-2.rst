.. |info| image:: media/info.png
   :width: 0.26667in
   :height: 0.26667in
.. |action| image:: media/action.png
   :width: 0.25in
   :height: 0.25in
.. |question| image:: media/question.png
   :width: 0.26667in
   :height: 0.26667in


*****************
Assembly analysis
*****************

In the presentation we will cover:

- Overview of MGnify annotation pipeline
- Taxonomic assignment
- Functional characterisation
- Pathways/systems
- Using the contig viewer

MGnify hands-on exercises
##################################

For this session we will look at some of the data and analyses that are available from MGnify. We will navigate the resource, try out different ways to search for interesting samples/studies, and then investigate the analysis results that are available for assemblies.

Browsing MGnify
****************

From the MGnify front page (https://www.ebi.ac.uk/metagenomics/) you can see various options to browse the data. There are quick links to the various data-types (e.g. amplicon, assembly, metagenomes, etc) we support, as well as a subset of the biomes that the data covers.

|action| Click on the "wastewater" biome icon.

|question| How many studies does MGnify hold that relate to wastewater?

|question| How many samples does that relate to?

|action| From the sample list, select the 3rd sample down (ERS1215575), and take a look at the metadata available.

|question| Do you know the exact location of where the sample was taken?

|question| What are the lat/long co-ordinates?

|question| Follow the link to the BioSamples record, can you find any more information about the location of the sample?

|action| From the tabs in the header bar, select **Text search**, and then select **Samples** below the search box. There are a number of metadata fields available to allow you to filter for a sample of interest to you. Not all are relevant to all samples. 
Within the hierarchy of biomes, navigate to environmental>aquatic>lentic. You should see 57 samples. Now select the depth filter.

|question| How many lentic samples have depth data associated with them?

|question| Using the sliders, can you identify a sample of a lentic water system from a depth between 25-50m?

MGnify assembly analysis
**************************

Now we will look at some assembly data that has been analysed by MGnify. 

|action| Search for **MGYS00003598**, and go to this study page. This is a large study where MGnify have assembled the raw reads from an existing public study. The list of assemblies is shown at the bottom of the study page.

|question| How many assemblies are included in this study?

|action| Click on the 2nd analysis link in the list **MGYA00510849**. You could alternatively search for this accession using the text search options. Have a look at the information within the **Quality control** tab.


|question| How many contigs are included in this analysis?

|question| What length is the longest contig in this dataset?

|action| Click on the **Taxonomic analysis** tab and examine the phylum composition in the graphs and the krona plot.

|question| What proportion of the total LSU rRNA predictions are eukaryotic? 

|question| What proportion of the bacterial predictions are proteobacteria?

|action| Click on the **Functional analysis** tab. The top part of this page shows a sequence feature summary, showing the number of contigs with predicted coding sequences (pCDS), the number of pCDS with InterPro matches, etc.

|question| How many predicted coding sequences (pCDS) are in the assembly? 

|question| How many pCDS have InterProScan hits? 

|action| Scroll down the page to the InterPro match summary section.

|question| How many different InterPro entries are matched by the pCDS? 

|question| Why is this figure different to the number of pCDS that have InterProScan hits? 

|action| Click on the **GO Terms** sub-tab. This shows a summary of the most common GO terms annotated to the pCDS as both bar charts, and pie charts.

|question| What are the top 3 biological process terms predicted for the pCDS from this assembly? 

|action| Have a look at the information in the **Pfam** and **KO** (KEGG orthologue) sub-tabs.

|action| Click on the **Pathways/Systems** tab. Have a look at the data reported in the 3 sub-tabs: KEGG Module, Genome Properties, and antiSMASH.

|question| How many KEGG modules are reported for this assembly? 

|question| How many of these are 100% complete (i.e. all of the constituent KOs are found)? 

|question| How many Genome Properties of the category **DNA handling**, are found within this assembly? 

|question| What is the most common class of biosynthetic gene cluster found in this assembly?

|question| How many non-ribosomal peptide synthetase gene clusters are identified by antiSMASH in this assembly?

|action| Click on the **Contig Viewer** tab. Load the data for the 4th contig in the list by clicking on the contig name (ERZ501066.4-NODE-4-length-276957-cov-33.799655). This contig will now be loaded into the viewer.

|question| How long is this contig? 

|question| The longest pCDS in the contig appears to start at 202339. What protein is coded for? 

|question| Looking at the antiSMASH annotations, where within the contig do any transport-related genes fall? 

|action| Zoom into that region to see the predicted regions in more detail. Have a look at the information about the various transport-related genes. 

|question| What region of the contig is predicted to code for a major facilitator transporter? 

|info| There are lots of different visualisation options available within the contig viewer. Take some time now to investigate the various options, and play about with it by looking at a few different contigs and the anotations they contain.
