---
description: 'Contributed by Reysha Patel, BENG183 2018 Fall. UCSD'
---

# Precision medicine

1. Introduction - What is Precision Medicine?
2. Overview of Precision Medicine/Pipeline 
3. Diabetes and Precision Medicine
4. Benefits and Drawbacks
5. Future of Precision Medicine
6. References

### 1. Introduction - What is Precision Medicine?

> Most medical treatments are designed for the "average patient" as a one-size-fits-all-approach, which may be successful for some patients but not for others. This is the way medicine has been approached for many years. Precision medicine, however, takes a new approach that tailors disease prevention and treatment to the differences in people's genes, environments, and lifestyles. The goal of precision medicine is to target the right treatments to the right patients at the right time.

The difference between personalized medicine and precision medicine:

> Although they are often used interchangeably, personalized medicine is more focused on the diagnosis and treatment of a single person rather than the use of big data to categorize diseases and determine specific treatments for subtypes to be applied to individuals on a larger scale.

### 2. Overview of Precision Medicine/Pipeline

> The first step in conducting precision medicine research requires collecting data from patients two groups of patients: a disease group and a control group. There are several bioinformatics approaches used to gather relevant patient data that can be applied to diagnosing and treating patients. Some popular approaches are:
>
> * High-throughput sequencing
> * RNA-Seq
> * Molecular profiling
> * Tumor profiling
> * Hi-C
> * Chip Seq  
>
> After data is obtained, the patients or disease is categorized according to the relevant features that were determined through data collection. This clustering is usually carried out using various machine learning algorithms. Finally, the appropriate treatments can be determined based on an individual basis or disease subtypes.\[3\]

![](../../.gitbook/assets/image%20%287%29.png)

![](imag.png) An overview of the basic precision medicine protocol described above can be seen in the figure above. **Figure by Prasad, Rashmi, et al. Journal of Internal Medicine \(2018\).**

### 3. Diabetes and Precision Medicine

> The treatment of diabetes has been lagging behind cancer for some time now because the diagnosis of diabetes during the last 100 years has been based upon measurement of a single metabolite, glucose. This method of diagnosis had lead to the classification of diabetes into two main subgroups - Type 1 \(T1D\) and Type 2 \(T2D\). These categorizations are very imprecise.
>
> T2D is an exclusionary diagnosis. If the patient does not have T1D or monogenic diabetes, then they are considered to have T2D. This suggests that about 90% of all patients with diabetes have T2D. Metformin generally the first medication that physicians prescribe to patients with Type 2 diabetes, as it controls insulin levels.
>
> However, not all patients diagnosed with T2D respond well to the treatments that are typically prescribed, like Merformin. To address this heterogeneity of T2D, a study, conducted in 2018 by Lund University Diabetes Center was able to classify Type 2 diabetes into five distinct subgroups, allowing for prediction, diagnosis, and ultimately treatment. Sub-classification of the disease resulted from their clustering analysis, which was based on six characterizations: age at diagnosis, BMI, HbA1c, GADA, C-peptide together with glucose for estimation of insulin secretion, HOMA-B and insulin-sensitivity, and HOMA-IS.

![](../../.gitbook/assets/image%20%2810%29.png)

This table shows the phenotypic characteristics that were used to create the T2D subtypes. **Figure by Prasad, Rashmi, et al. Journal of Internal Medicine \(2018\).**

#### Type 2 Diabetes Subtypes

**SAID \(Severe autoimmune diabetes\)**

SAID is severe autoimmune diabetes. It is characterized with the presence of GADA, low insulin secretion, and poor metabolic control. SAID shows the expected association with HLA genes, which is completely lacking in SIDD.\[1\]

**Treatment**

Insulin

**SIDD \(Severe insulin-deficient diabetes\)**

SIDD is severe insulin deficient diabetes. SIDD is characterized with characterized by low insulin secretion, poor metabolic control, and an increased risk of retinopathy. SIDD also shows a strong association with variants in the TCF7L2 gene \(which has previously shown strong association with T2D and insulin deficiency\).\[1\]  


Treatment: Mistreated by Metformin and need insulin.

**SIRD \(Severe insulin resistant diabetes\)**

SIRD is severe insulin resistant diabetes. It is characterized by was characterized by severe insulin resistance, obesity, late onset and markedly increased risk of nephropathy. SIRD reflects an “unhealthy” obesity with insulin resistance and often fatty liver. In support of this, SIRD shows a clear association with a variant in the TMSF2 gene previously associated with fatty liver and nonalcoholic fatty liver disease.\[1\]   


Treatment: Need treatment which enhances insulin sensitivity

**MOD \(Mild obesity related diabetes\)**

MOD is mild obesity related diabetes represents healthy obesity with no insulin resistance. It is characterized by obesity, early onset and good metabolic control\[1\]

Treatment: Lifestyle, Metformin

**MARD \(Mild age related diabetes\)**

MARD is mild age related diabetes. It is characterized by late onset and good metabolic control.\[1\]  


Treatment: Lifestyle, Metformin.

![](../../.gitbook/assets/image%20%2816%29.png)

These plots show the results of the K-means clustering algorithm that was used to create the five diesease subtypes in diabetes. **Figure by Ahlqvist, Emma, et al. The Lancet Diabetes & Endocrinology \(2018\)**

### 4. Benefits and Drawbacks of Precision Medicine 

> Since precision medicene is upcoming there are many benefits and drawbacks associated with precision medicene. These benefits and drawbacks are related to a variety of different fields including governmental policy and scientific practices.

**Benefits** 

* Treatments that are derived as a result of precision medicine are more likely to be successful because there are many additional tests that are performed to determine the specific subtype of disease. These tests allow treatment to be more specific and to better target the disease.
* Another benefit of the genetic testing involved with precision medicine is that the treatment is less likely to have side effects because it is tailored to a specific disease subtype.
* Precision medicine can also be used as a means of early diagnoses. For example if a patient is beginning to exhibit a genetic change that is common  in a certain disease that patient can be diagnosed early.
* It can also be used as preventative medicine in the example of breast cancer, where the BRCA genes are indicators that a patient may develop breast cancer.
* All of the testing in precision medicine also can help determine new disease subtypes which we saw in our diabetes example.
* Precision medicine can also reveal population health, in that we can see which countries or groups of genetically similar people are likely to develop a specific disease. \[4\]

**Drawbacks** 

* A big drawback of precision medicine is that is expensive. Testing is expensive and precision medicine is based on the idea of genetic testing.
* All of the testing is also very time consuming. The testing itself is quick, but the sequencing and secondary analysis of data is very time consuming because the files are large.
* The large files created by the different types are testing could lead to a data storage problem. These files tend to be very large and testing every patient would create a data storage problem.
* Many of the informatics approaches that are already in place are not able to effectively integrate data, informatics approaches need to be better developed and improved so that data that is collected can be analyzed effectively.
* Precision medicine involves patient data is heavily protected and hard to access. As testing becomes more common, patient privacy may be an issue and the security of their information could also be at stake.
* Many current precision medicine approaches and studies are difficult to access. So there is limited access to collected data as well.\[4\]

### 5. Future of Precision Medicine

> Current studies utilizing precision medicine are barely scraping the surface of the capabilities of the practice. As a relatively new approach in determining both diagnoses and treatments for many diseases, precision medicine has room for growth in so many areas. For researchers, having access to appropriate and complete patient data is imperative to determining diagnosis and treatments that are accurate and can be useful in a clinical approach. Furthermore, besides HIPAA \(Health Insurance Portability and Accountability Act\), there is not much policy in place to protect patient's genomic data which has the potential to be used without the patient's full consent. Finally, many of the informatics approaches that are currently used to cluster patient data are time consuming and inaccurate, so the advent of new informatics approaches is a key factor in furthering the field of precision medicine. More specific examples of ways in which these areas are progressing towards a future of clinical applications are listed below
>
> **Data Collection**
>
> The All of Us Research Program is an initiative that began in 2015. The program was given $215 million in funding and it aims to collect the various forms of data, such as sequencing information, physical examination data, and wearable device information in order to make advances in tailoring medical care to the individual.

Research institutes, like Memorial Sloan Kettering, are also at the center of creating an infrastructure for widespread access to certain aspects precision medicine. Sloan Kettering is attempting to do this for cancer research and treatments by grouping patient data which can determine patient eligibility for clinical trials.

A large amount of data is also being collected through the use of mobile or wearable devices. For example, the Fitbit, collects lots of valuable information about health and fitness. This data could prove to be extremely useful in a clinical setting.

**Policy**

In addition to the need for legislation in the area of patient privacy regarding genomic and other health related information, there is also a need for increased funding in the area of precision medicine. As more money has been allocated towards research in precision medicine has increased in the past few years, the reimbursements for those who wish to participate in studies or clinical trials remains low.

**Better Informatics Approaches**

Machine learning is widely applied in solving health informatics problems because it is able to make predictions based on large datasets. Various machine learning algorithms are able to reduce data dimensionality and determine features that are relevant in applying treatments and diagnoses. However, sometimes complex data, lack of data, or rare events, \(which are highly probable in patient data\) are not able to be accurately handled using machine learning algorithms. For this reason, better informatics approaches are needed for reaching accurate clinical results.

Data storage is an additional area in expansion is needed in order to keep up with growth in precision medicine. Human data is very large and must be protected so abundant and secure databases will need to be established to store patient data.

### 6. References

\[1\] Prasad, Rashmi B, and Leif Groop. “Precision Medicine in Type 2 Diabetes.” _Journal of Internal Medicine_, 2018, doi:10.1111/joim.12859.

\[2\] Ahlqvist, E., et al., "Novel subgroups of adult-onset diabetes and their association with outcomes: a data-driven cluster analysis of six variables." _Lancet Diabetes Endocrinology_, 2018. 6\(5\) p. 361-369   


\[3\] Center for Devices and Radiological Health. “Precision Medicine.” _U S Food and Drug Administration Home Page, Center for Drug Evaluation and Research_, 2018, www.fda.gov/medicaldevices/productsandmedicalprocedures/invitrodiagnostics/precisionmedicine-medicaldevices/default.htm.  


\[4\] Patel, Kirti. “Precision Medicine: Pros & Cons – Kirti Patel, MD – Medium.” Medium.com, _Medium_, 1 Feb. 2015, medium.com/@kirtipatelmd/precision-medicine-blessing-or-curse-8722c3ae94cb.

