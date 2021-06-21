# Dog Breed Catalog :dog::dog::dog:


In this project, we extracted data from different sources to get information about different dog breeds, to get physical characteristics, activity levels, and temperament that make each dog breed unique. Having a centralized database might help veterinarians, dog enthusiasts, or future dog owners. 


![puppies](https://user-images.githubusercontent.com/80076539/121785148-20b94100-cb86-11eb-9e40-671d93426109.jpg)

## Team Members

* Mariana Geffroy López 
* Carlos Iván Hernández 
* Omar Rivera Galván
* Jose H. Sierra 
* Pablo Villalpando Álvarez

## Original data Sources: 

#### For Data Scraping:

* American Kennel Club: https://www.akc.org/
* Breed Profiles dogtime.com: https://dogtime.com/dog-breeds/profiles

#### Table Data Scraping: 

* Winners Westminster Dog Show: https://en.wikipedia.org/wiki/List_of_Best_in_Show_winners_of_the_Westminster_Kennel_Club_Dog_Show
* Winners National Dog Show ( USA): https://en.wikipedia.org/wiki/National_Dog_Show

#### Dog API: 

* Images from: https://www.thedogapi.com/

#### CSV databases (From Kaggle and data.world): 

* best_in _show.csv (Breed, Category, Popularity in the US, Lifetime Cost)
* dog_breeds.csv (Breed Name, Alt Breed Name, Group 1, Group 2, Male Weight, Temperament, Puppy price, Intelligence, Watchdog). 
* dog_weight_lenght.csv (Breed, height_low_inches,height_high_inches,weight_low_lbs,weight_high_lbs)


## Project Report :dog2::dog2::dog2:

### Extract

1.- Official and accepted dog breeds were scraped from the webpage of the American Kennel Club. https://www.akc.org/ using Soup and Splinter. First, in the main page, each url for each letter was scraped and visited, and in each letter (‘A’, for example), we scraped all breeds corresponding to that letter (Affenpinscher, Afghan Hound, Airedale Terrier) with a short description and created a list of dictionaries for every breed.

2.- Pet´s social characteristics for each breed were also scraped from dogtime.com. These come in star-ratings, where we obtained a score from 1 to 5.https://dogtime.com/. An important thing to note is that the scraping was performed based on the previous list of breeds. 

3.- Dog databases were searched for in Google, Kaggle and data.world. Databases with fields relevant to dog characteristics, price and popularity were chosen and downloaded. These were stored in the Resources folder.  

4.- Information about past dog show winners was found in Wikipedia. Tables with the winners and breed were scraped and converted to csv files. 
Westminster Kennel Club Dog Show 
National Dog Show

5.- Dog images were retrieved using https://www.thedogapi.com , where we first looked for information of a certain breed (in breeds tab of the API) and extracted the corresponding image url, then went to image tab of the API and performed requests with the url obtained before.

### Transform

Past show winner tables were cleaned to just have three variables, year, winner and dog-breed using read_html, value counts and filters.

For the American Kennel Club and DogTime we used web scraping methods:
Splinter setup.
We used soup.find_all to get the elements needed and included inside for loops to get the dog breeds on each one.
We looped all records from the list_dictionary to include information from both lists.

Finally we used https://api.thedogapi.com to get all the images available for each breed in the previous dictionary.

### Load

The final database was loaded into MongoDB. We chose a Non-Relational Database due to the differences in our data. There is a large amount of data for popular breeds, but for others, there are not as many records. At the same time, we have some non-conventional data like: URLs to some images or large strings that would not fit correctly in a regular relational database. 

## Contents 
### Resources folder  :file_folder:
- **best_in_show.csv**: CSV file that contains different brees with their characteristics, popularity and price. 
- **dog_breed_characteristics.csv**: CSV file that contains breed names and characteristics.
- **Dog_weight_length.csv**: CSV file that contains the maximum and minimum weight and length of different dog breeds.
 
#### Dog_show.ipynb:
Script that scrapes tables with the winners of the National Dog show and the Westminster Dog Show. 
#### Dog catalog.ipynb: 
Script that scrapes data from different webpages and then creates a database with main dog characteristics divided by dog breed. 

- - -
