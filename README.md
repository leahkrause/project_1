# project_1

README

Objective: Analyze the prevalence of allergies/sensitivities of the most common food allergens for a sample population of children with different ages, ethnicities, races and birth years (ranging from 1983 to 2012).

Our analysis is motivated by the desire to bring awareness to the food industry and the general public about allergy risk that may be caused by the most common food allergens.

Common Food Allergens
Peanuts
Milk
Eggs
Shellfish
Soy
Fish
Wheat
Sesame
Tree nuts*


Tree nuts* includes: walnut, almond, hazelnut, pecan ,brazil nuts, cashew and pistachio. 

Question Addressed:

Has the prevalence of food allergies increased over time?
What is the likelihood of allergens in each demographic? 
Are certain allergies correlated?
Does population density define the severity level of reactions?

Data Source: We used the Kaggle CSV file (food-allergy-analysis-Zenodo.csv) to create the allergy dataframe.

The columns we used for the analysis are:
BIRTH_YEAR
The patient’s birth year
AGE_START_YEARS
The age of the patient tested for the first time
AGE_END_YEAR
The age of the patient tested for the last time
[allergen*]_START_YEAR  
The first year the allergy test started
[allergen*]_END_YEAR
The last year of the allergy testing
[allergen*]_ALG_START 
Allergy response number at the beginning of the test
[allergen*]_ALG_END  
Allergy response number at the end of the test

*allergen includes:[ SHELLFISH, FISH, MILK, SOY, EGG, WHEAT, PEANUT, SESAME, WALNUT, PECAN, PISTACH, ALMOND, BRAZIL, HAZELNUT, CASHEW ]


          [allergen*]_ALG_START/[allergen*]_ALG_END Columns:
 
Allergy response number ( IgE reactivity level)  is the measure that  shows the level of antibodies produced after being exposed to the allergen. It shows how strong your immune system reacts to the allergen.The numbers in the [allergen*]_START_YEAR and [allergen*]_END_YEAR   columns are interpreted according to the following table:





The dataset includes a large number of ‘NA’ entry values. Since each patient is not necessarily allergic to all allergens, for those particular allergy columns which the response is not applicable they put NA. This NA is not supposed to drop, and is considered as ‘no antibodies for allergens’.

There are some wrong entries (negative values) for BIRTH_YEAR, AGE_START_YEAR, AGE_END_YEAR,.. which were removed from the table.

Exploration Process:
Demographic Overview
To find the demographic distribution of data, we used the statistical description of each demographic column(gender, race, ethnicity) and displayed it in the following charts:
  



According to the demographic distribution charts, populations are almost equally distributed in terms of gender.  Ethnicity is mostly non-Hispanic (95.4%). Race has a very low percentage in Asian/pacificIslander(2.7%) and other undefined races(12.9%). Black and white races are the most populated ones.
To analyze the prevalence of reported allergy cases in the past years, as shown in the following table, 25% of cases are between 1983-1996 while from 1996 till 2000, in 6 years, the reported cases are doubled. From 2002 to 2007, in 5 years, again we see the same pattern and in 2012 we have the maximum cases. 

 

Another study is about the starting age of the allergy. Is a certain age range more reported in the dataset? We explored each allergen separately, the allergens had similar behavior. In the following   graph(We plot the data for the peanut), the younger kids (babies, toddler, and preschooler) have more cases than other children. For older kids we have less cases which are reduced as they get older. It also has the same pattern for different races.


From the summary table, more than 50% of the population reported their cases before the age of 2 and 75% reported around the age of 7.  


Initial Processing:

 By calling the ‘get_alergen ( allergen_name )’ function we can create the allergen dataframe and explore and analyze each specific allergen independent of others. It helps us to focus only on the patients with this particular allergen without involving the NA entries of other allergens.

<!-- 
def clean_DataFrame(allergen):
    allergen_start_column=allergen.upper()+'_ALG_START'
    allergen_end_column=allergen.upper()+'_ALG_END'
    
    allergen_df=allergy_df[['SUBJECT_ID', 'BIRTH_YEAR', 'GENDER_FACTOR', 'RACE_FACTOR',
       'ETHNICITY_FACTOR', 'PAYER_FACTOR', 'ATOPIC_MARCH_COHORT',
       'AGE_START_YEARS', 'AGE_END_YEARS', allergen_start_column,
       allergen_end_column]].copy()

    allergen_df_clean=allergen_df[(allergen_df[allergen_start_column].isna()==False)]
    allergen_df_clean.reset_index(inplace=True,drop=True)
    
    return allergen_df_clean
 -->
	 	



