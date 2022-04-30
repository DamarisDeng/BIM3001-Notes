# BIM3001 Notes

## Cytoscape

1. Objective: Draw protein-protein interaction network

2. Materials: a list of protein (gene) of interest (leukemia_selected.txt)

   ```
   NAME	SCORE
   TCL1A	3.2364633
   DNTT	2.7405555
   CD24	2.2931862
   CD79B	1.9089864
   CRIM1	1.8777686
   MME	1.83437
   BLNK	1.767103
   TOP2B	1.7252915
   ```

3. Usage: (with string database)

   1. Search the group of protein in [STRING](https://string-db.org/), in this task, we choose **multiple proteins**, choose **Homo Sapien** as organism

      (it's ok to input the score inside the search box)

   2. Review the list of proteins and click `continue`

   3. A network will appear. Click `Exports` as `.tsv` (the one that can be opened in Excel and Cytoscape)

   4. Open Cytoscape

   5. Import `.tsv` file into Cytoscape using `import network from file system`, <img src="/Photos/Import network.png" alt="Import network" style="zoom:50%;" />

   6. A network will appear. Then import table from file <img src="/Photos/Import table.png" alt="Import table" style="zoom:50%;" />, choose `import to node columns` 

      ![Node table columns](/Photos/Node table columns.png)

   7. Now the node table will have a new column  

      ![new column](/Photos/new column.png)

   8. Then change the style. Here, we map the **color of nodes** to the **differential expression score**, and map the **width** of edge to the combined score (calculated by string, based on experiments and algorithms)

   9. Finish drawing. Export the image.

   ![OutputFigure](/Photos/OutputFigure.png)

4. Summary

   1. Distinguish the node attribute and edge attribute when importing data.
   2. I want to try command line~
   3. Can try R or Python to design Cytoscape automation!



## GSEA

[GSEA Official Website](https://www.gsea-msigdb.org/gsea/index.jsp)

1. Objective: Conduct gene set enrichment analysis

2. Preparations (files)

   [data formats introduction](https://software.broadinstitute.org/cancer/software/gsea/wiki/index.php/Data_formats)

   1. `.gct` file (database) (不是很懂)

      ```
      #1.2
      10056	48
      NAME	DESCRIPTION	ALL_1	ALL_2	ALL_3	ALL_4	ALL_5	ALL_6	ALL_7	ALL_8	ALL_9	ALL_10	ALL_11	ALL_12	ALL_13	ALL_14	ALL_15	ALL_16	ALL_17	ALL_18	ALL_19	ALL_20	ALL_21	ALL_22	ALL_23	ALL_24	AML_1	AML_2	AML_3	AML_4	AML_5	AML_6	AML_7	AML_8	AML_9	AML_10	AML_11	AML_12	AML_13	AML_14	AML_15	AML_16	AML_17	AML_18	AML_19	AML_20	AML_21	AML_22	AML_23	AML_24
      ```

      ![Intro to gct file](/Photos/Intro to gct file.png)

   2. `.cls` file (phenotype labels)

      ```
      48 2 1
      # ALL AML
      ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL ALL AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML AML
      ```

​				![Intro to cls](/Photos/Intro to cls.png)

3. Steps

   1. Load data (Load the files from local environments to GSEA)

   2. Click `Run GSEA`

   3. Set parameters

      ![Parameter setting in GSEA](/Photos/Parameter setting in GSEA.png)

      1. Expression dataset: load `.gct` file

      2. Gene sets database (biological functions/pathway database): Can choose online and local database, more than one database can be chosen. [Check all the databases here](https://www.gsea-msigdb.org/gsea/downloads.jsp). The most widely used file is `.gmt` file

         [^1]: When multiple databases are chosen, you need to make sure that no item is repeated. Or error will rise.

      3. Number of permutations: higher = more accurate, usually 1000 is enough
      4. Phenotype labels: load the `.cls` file

      5. Collapes/Remap to gene symbols: As described in the figure

   4. I don't know much about basic fields and advanced fields parameters

   5. Click `Run` and wait for the result.



## Motif Searching

JASPAR, MEME
