The code is in brazilian portuguese and is together with the portuguese version of the documantion.

O código está escrito em português e está junto com a versão em português da documentação.

# Brazilian National High School Exam Data Analysis
Project to analyze data of brazilian national exam for high school students. The data is available by education departament of brazilian government. The intent of this project was to develop familiarity with Pandas library. 

# Overview

In order to learn how to manipulate data with the `Pandas` library, an analysis of the ENEM data was carried out to answer two main questions:
- Percentage of correct answers per question and how much this reflects on the previous defined difficulty level of each question
- Number of hits per note, so that it is possible to establish a relationship between these magnitudes and observe outliers

# Understanding the exam and database

ENEM is an acronym for National High School Examination.
As the name implies, it consists of a test held every year by the Brazilian government to assess the knowledge of students graduating from high school.
The test consists of 4 areas of knowledge:
- Human Sciences and their technologies
- Natural Sciences and their technologies
- Languages, Codes and their technologies
- Mathematics and its technologies
- Essay

With the exception of Writing, until the 2022 edition, the tests were multiple choice. The grade is assigned based on the [IRT](https://gauchazh.clicrbs.com.br/educacao-e-emprego/noticia/2021/11/como-funciona-a-tri-na-avaliacao-do-enem-ckw3zwd9c004a016fuvd3uu6k.html). So two people with the same number of correct answers do not necessarily get the same grade. According to how the IRT works, getting easier questions right add more points to the final grade than getting difficult ones.

# The problem

Based on this, very relevant questions emerge among students:
- What are the easiest questions, and therefore, the ones that I should get more right?
- What is the average ratio of correct answers x grades?
- How many questions do I need to get right so that my grade is between X and Y?

The only database we have access to is the [ENEM Database](https://www.gov.br/inep/pt-br/acesso-a-informacao/dados-abertos/microdados/enem). The document contains information about the public notices, the methods applied for evaluating the IRT and information on applicants, such as socioeconomic information, the code and color of the test taken by each applicant, as well as their answer and the corresponding grade (both in a string. Ex: "ABBBDE..").
Given the national dimension of the test, the data are very extensive, reaching 5 million lines.
In addition, there is a smaller file with data referring to the questions, which inform the question code, in which tests it appears and in what order it appears, its level of difficulty (used by IRT to assign a grade), among other parameters.
However, there are no direct answers to the questions mentioned above.
This notebook contains a code precisely to carry out this analysis and bring answers.

# Code working

The main operations performed by this code are:
1) Filter only students who took the 5 tests consistently, that is, they did not score zero, missed or canceled any test.
2) For each student, compare the feedback and response strings to count the number of correct answers and count the number of correct answers for each question.
3) Sort questions based on percentage for easiest and hardest lists.
4) Build histograms and graphs to analyze the ratio of hits and grades, with that, look for minimum and maximum hits for a target note, or doing the opposite process, look for maximum and minimum scores for a number of target hits.
5) Finally, secondary analyzes for the purpose of this project can be carried out: relationship between grade and socioeconomic level, year of graduation in high school, among other parameters.

The structure of what is to be done itself is simple. The greatest difficulty encountered was how to organize and standardize all the data. The same test has several versions, with questions in different orders. Therefore, for two answers from two students, "AABBB.." and "ACDDEA..", it does not mean that the questions in position 0 of the string are the same, the tests can have different colors and this must be checked at each count.
In addition, there are cases in which, due to disasters and other problems on the day of the application, the test is applied on another day, so there are two tests with a set of completely different questions and without any intersection. Other, more specific details emerged and had to be dealt with, such as the choice of Spanish or English in the tests, which affects the format of the response string.

# Outputs

I published [spreadsheets](https://drive.google.com/drive/folders/1yVT-PJZ7oHBNL1bGHtw22vdQh4r-DzYS?usp=sharing) with more interesting graphics and results from the point of view of people who are preparing for the test. The access to them is free.

I also published a video (currently offline for technical reasons) showing the analysis. It is not a tutorial for code development! But it explains what was done, how the data works, shows the final data being explored and shows how to use the spreadsheet.
