# Users’ Manual of RECWAS (Version 1.0.0)
Random Effect Cistrome-Wide Association Studies (RECWAS): Leveraging Random Effects in Cistrome-Wide Association Studies for Decoding the Genetic Determinants of Prostate Cancer.

## Overview of RECWAS
RECWAS is a kernel-based association approach that connects genetic variants to disease by mediating cistrome. It utilizes genotype and ChIP-seq data and consists of two principal components. Firstly, in the training phase, the weights between single nucleotide polymorphisms (SNPs) and cistrome are calculated using linear models such as lasso or by considering the marginal effect of the SNPs. Secondly, RECWAS employs a kernel machine-based feature aggregation for cistrome-disease association testing, which captures the non-linear interaction among SNPs. In both simulated and actual analysis, RECWAS demonstrates robust ability in pinpointing disease susceptibility regions and uncovering previously unrecognized disease-associated regions. This has profound implications for our understanding of the genetic basis of prostate cancer and potentially other complex diseases, offering a more nuanced and comprehensive genomic analytical tool.<br>
![RECWAS](https://github.com/PrecisionWAS/RECWAS/blob/main/RECWAS_Overview.png)<br>

## Usage of RECWAS
RECWAS is a batteries-included JAR executable. All needed external jar packages are included in the downloadable, `RECWAS.jar`. 

- **Download**
  - To download all necessary files, users can use the command<br>
  `git clone https://github.com/PrecisionWAS/RECWAS.git`

- **Required software and R packages**
  - PLINK v1.9 (https://www.cog-genomics.org/plink/)
  - R software (https://www.r-project.org/)
  - SKAT >= 2.2.5 (https://cran.r-project.org/web/packages/SKAT/index.html)

- **Usage**
  - ```java
    java  -jar  RE-CWAS.jar  RE-CWAS  -format  plink|csv  -input_genotype  path/to/example.tped|example.csv  -input_phenotype  path/to/example.tfam|example.tsv  -input_phenotype_column  6|2  -input_phenotype_type  continuous|binary  -weights_info  path/to/CWAS_AR_top1.txt  -gene  chr2:100092500-100093200  -plink  path/to/plink  -Rscript  path/to/Rscript  -output_folder  path/to/output_folder
    ```

- **Arguments**
  - **format:** the format of genotype and phenotype data, plink or csv.
  - **input_genotype:** genotype file.
  - **input_phenotype:** phenotype file.
  - **input_phenotype_column:** the column of phenotype in the phenotype file.
  - **input_phenotype_type:** the type of phenotype, continuous or binary.
  - **weights_info:** weights file between SNPs and cistrome.
  - **gene:** the name of cistrome peak.
  - **plink:** plink command path.
  - **Rscript:** Rscript command path.
  - **output_folder:** path of the output file.

- **example**
  - After 'git clone', user can try our example data in the EXAMPLE folder by using<br> 
  ```java
  java  -jar  RE-CWAS.jar  RE-CWAS  -format  csv  -input_genotype  EXAMPLE/csv_format/example.csv  -input_phenotype  EXAMPLE/csv_format/example.tsv  -input_phenotype_column  2  -input_phenotype_type  binary  -weights_info  WEIGHTS/CWAS_AR_top1.txt  -gene  chr2:100092500-100093200  -plink  path/to/plink  -Rscript  path/to/Rscript  -output_folder  path/to/output_folder`<br>
    ```
  or<br>
  ```java
  java  -jar  RE-CWAS.jar  RE-CWAS  -format  plink  -input_genotype  EXAMPLE/plink_format/example.tped  -input_phenotype  EXAMPLE/plink_format/example.tfam  -input_phenotype_column  6  -input_phenotype_type  binary  -weights_info  WEIGHTS/CWAS_AR_top1.txt  -gene  chr2:100092500-100093200  -plink  path/to/plink  -Rscript  path/to/Rscript  -output_folder  path/to/output_folder`
    ```

- **NOTE**
  - To consistent with plink format, the phenotype is set to missing (normally represented by -9) if unspecified. It must be a numeric value. Case/control phenotypes are normally coded as control = 1, case = 2.The association `RECWAS.result` under `path/to/output_folder` is the final output file by RECWAS. More description and benchmarking of RECWAS can be found in our manuscript.

## Citations
If you use the CWAS weights in analysis, please cite:<br>
**Genetic determinants of chromatin reveal prostate cancer risk mediated by context-dependent gene regulation, Baca et al., 2022, Nat Genet** <br>
If you use the RECWAS software in analysis, please cite:<br>
**Leveraging Random Effects in Cistrome-Wide Association Studies for Decoding the Genetic Determinants of Prostate Cancer, Mengting et al.,**<br>

## Contacts
Chen Cao : caochen@njmu.edu.cn<br>
Ning Gu  : guning@nju.edu.cn<br>

## Copyright License (MIT Open Source)
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT
NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE. 
