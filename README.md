# cognitive-impairment-SABE

## Code by Fabiana Ribeiro for BMC Geriatrics, doi:10.1186/s12877-021-02542-x
Please cite this paper when using the code: 
Ribeiro, F. S., Duarte, Y. A. d. O., Santos, J. L., F., & Leist, A. K. (2021). Changes in the prevalence of cognitive impairment and associated risk factors 2000-2015 in São Paulo, Brazil. BMC Geriatrics. https://doi.org/10.1186/s12877-021-02542-x 

## Data availability
This paper uses data from the SABE study. The datasets generated and/or analysed during the current study are not publicly available due to privacy and ethical restrictions but are available from the corresponding author on reasonable request.

## Funding
This work was supported by the European Research Council (grant agreement no. 803239, 2019–2024, to AKL).

## Main Code Details
We use the original data from the four waves of SABE study (Health, Well-Being, and Aging) 2000, 2006, 2010, and 2015 with the weights for each wave. Data of each wave was merged into one dataset. 

### Variable Descriptions

`agegroup` participant's age categories (60-64, 65-69, 70-74, 75-79, 80-84, and ≥ 85 years) recoded from ` a01b ` in the original main file

`year` SABE years of data collection (2000, 2006, 2010, and 2015) created in the merged dataset
`sex` participant's sex (male/female) categories recoded from ` c18` in the original main file

`race` participant's race (White, brown or mixed, black, and other) categories recoded from ` a12 ` in the original main file

`educdet` participant's educational level (no education, primary, secondary, and post-secondary) categories recoded from ` a06n` in the original main file

`income` individual income as the number of times the national minimum wage (< 1, 1-2, 2-3, 3-4, and > 4) categories recoded from ` rendatot ` in the original main file

`heartdisease` participant's self-reported heart disease categories recoded from ` c08 ` in the original main file

`diabetes` participant's self-reported diabetes categories recoded from ` c05 ` in the original main file

`stroke` participant's self-reported stroke categories recoded from ` c09 ` in the original main file

`hypertension` participant's self-reported hypertension) categories recoded from ` c04 ` in the original main file

`BMI_class` participant's body mass index (<18.5, 18.5-24.9, 25-29.9, 30+) categories calculated with the weight and height recoded from ` k11 ` and ` k05 `   in the original main file, respectively. 

`depression` participant's depressive symptoms assessed using the abbreviated Geriatric Depression Scale) categories recoded from ` depsoma ` in the original main file

`CImp` Cognitive impairment – MMSE- recoded from ` b09 ` in the original main file and 
 corrected by formal education years. 

`panel` participant's prior test exposure coded as 0 or 1

### Weighted analyses

`svyset setor [pweight=pmf] `

### Rao-Scott analyses

```
svy: tab agegroup year, percent col format(%12.1f) ci
svy: tab sex year, percent col format(%12.1f) ci
svy: tab race year, percent col format(%12.1f) ci
svy: tab educdet year, percent col format(%12.1f) ci
svy: tab income year, percent col format(%12.1f) ci
svy: tab heartdisease year, percent col format(%12.1f) ci
svy: tab diabetes year, percent col format(%12.1f) ci
svy: tab stroke year, percent col format(%12.1f) ci
svy: tab hypertension year, percent col format(%12.1f) ci
svy: tab BMI_class year, percent col format(%12.1f) ci
svy: tab depression year, percent col format(%12.1f) ci
svy: tab CImp year, percent col format(%12.1f) ci
```

### Logistic regressions

```
svy: logistic CImp i.agegroup
svy: logistic CImp i.year
svy: logistic CImp i.year i.agegroup
svy: logistic CImp i.year if agegroup==1
svy: logistic CImp i.year if agegroup==2	
svy: logistic CImp i.year if agegroup==3
svy: logistic CImp i.year if agegroup==4	
svy: logistic CImp i.year if agegroup==5
svy: logistic CImp i.year if agegroup==6`	
```
```
svy: logistic CImp i.year i.agegroup i.sex i.race i.income i.panel`
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression if agegroup==1
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression if agegroup==2
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression if agegroup==3
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression if agegroup==4
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression if agegroup==5
svy: logistic CImp i.year i.agegroup i.sex i.race i.panel i.hypertension i.diabetes i.income i.heartdisease i.stroke i.BMI_class i.depression if agegroup==6
```
