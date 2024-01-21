HW 2, CS 625, Fall 2023
================

Sahithi Padidela

Sep 20,2023

***Part 1 -- Data Cleaning***

Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly formatted, duplicate, or incomplete data within a dataset.

I have done the following steps below for data cleaning.

Import petnames.tsv and create a new project.

For the column, “What kind of pet is this”; click on the triangle on the
left side –\> select edit column –\> then, cluster and edit.

Using key collision method and fingerprint keying function,

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Image1.jpeg)

Using key collision method and ngram-fingerprint keying function,

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Image2.jpeg)

Using key collision method and metaphone3 keying function,

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Image3.jpeg)

Using key collision method and Daitch-Mokotoff keying function,

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/Image4.jpeg)

Using key collision method and Beider-Morse,

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/image5.jpeg)

Using  Nearest neighbor and Levenshtein

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/image6.jpeg)

After clustering and editing, I have used facet–\>text facet on “Pets age” column in the file.

Since the pets' ages include both texts and numbers, I changed them to solely numbers because age is expressed in numbers.
I have done it through expression ---> (value.replace(/[^0-9.]/, ''). 

After this i have used facet–\>text facet on “Pets breed” column in the file.
As we have empty columns in pets breed column,  I have replaced them with "unknown "keyword using the expression ----> if(isBlank(value),"unknown",value).

Now, to convert the pet’s age of all the pets to years, i have done manual editing based on some Expressions in Text facet column. Here we converted the age of the pet from their date of birth to age in numerics.



**Part 2. Analyze Cleaned Data**

Use the cleaned data to answer the following questions in your report
(and explain how you arrived at the answers):

1 . How many types (kinds) of pets are there?

 There are 23 kinds of pets available after cleaning the data.
![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/a.png)

2 . How many cats?

In 'What kind of pet is this' Column, Click the triangle on the left side, then select Facet --->Custom text facet..

 Then select Language as General Refine Expression Language(GREL)
 
 Type the Expression as value.contains("Dog") and then press ok.
 
 We get a text facet on the left side.Therefore the number of Cats are 503.
    
  ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/b.png)

3 . How many breeds of cats?

  After Cleaning the data,I have selected what kind of pet is this,then moving to pets breed 
  I applied text facet and on the left side of the screen it shows the number of choices for Cats i.e 169
  
  ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/c.png)


4.  What's the most popular cat breed? How many cats are in that breed?
  
      The most Popular Cat breed is Domestic short hair. There are 38 cats in that breed.
   
   ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/d.png)

   

 5. What's the age range of the cats?


     When Selected the Sort option and upon choosing the largest first we get the oldest cats's age which is 24,
     and upon choosing the smallest we get the youngest cat's age is 0.1.
     
     ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/5-2.png)
     
     ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/5-3.jpeg)
     
     ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/5-1.png)
    
      ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/5-4.jpeg)

 6. What's the age range of the rabbits? (Don't forget to look for bunny, too.)
 
     Upon choosing the Rabbit in the text facet of what kind of pets and then moving to pets age column to select sort and selecting smallest age the range is visible from smallest to 
      largest.
     Age range of the Rabbits is from 1.75 to 13.
    
     ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/6-1.png)
    ![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/6-2.png)

  7. What is the oldest pet? Give the pet's name, kind, and age.

     When Selected the Sort option and upon choosing the largest first we get the oldest pet's age which is bruse age 24.

     Pets name - Bruce Springsteen

     Kind - Cat

     Age -24

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/7-1.jpeg)



8 . What are the top 5 most popular dog breeds? List the breed and number.

   Top 5 most popular dog breed

    1 Golden Retriever(163)

    2 Mutt(35)

    3 Unknown(27)

    4 Labrador Retriever(22)

    5 Beagle(19)

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/8.png)

9 . What's the most popular everyday name for a dog?

The most popular everyday name for dog is Charlie.

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/9.png)


10. What's the most popular full name any pet?

The most popular full name pet is Bella.

![image](https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/10.png)

Files:


Cleaned Csv - <https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/HW2-petnames.csv.xls>

Operations used to clean the data in JSON format - <https://github.com/odu-cs625-datavis/fall23-mcw-SahithiPadi001/blob/main/HW2-petnames.json.json>




    
     
  











