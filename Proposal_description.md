# 1. Desires and aims

## 1.1. Introduction

Movies play an essential role in our lives, applying a deep influence on our emotions and social fabric. The extent of our engagement with a cinematic character is often related on the extent to which we can sympathize with the protagonist. Cinematic scenes or entire films may serve as an example that each of us refers to illustrate our values and objectives. In my opinion, cinema primarily serves as a form of entertainment and a stimulus for social interaction, facilitating discussions and conversations among peers.

The idea for this study arose from the discourse initiated by Mr. Martin Scorsese that "superhero movies aren't real cinema, that they lack real characters and ideas, and that other serious filmmakers can't get their films made because of superhero films"(The New York Times website). It is noteworthy that Mr. Scorsese is one of my favorite filmmakers, and his memorable impact on the movie industry is beyond dispute.

This project seeks to demonstrate whether there has been a noticeable shift in the cinematic preferences of the viewers. Do we prefer more action and less drama, or the superhero movies selling more in consequence of other various factors?

## 1.2. Aims and objectives

In this research proposal, it is essential to acknowledge that the final objectives may undergo modifications or refinements as the project is still developing.

The objectives of this proposal can be outlined as follows:
- Database Creation: The primary goal is to construct a suitable database by collecting data from the website: https://www.boxofficemojo.com/. This data will concentrate on the total gross revenue of movies.
- Genre Classification: A secondary aim is to categorize each movie according to its genre.
- Database Preparation for Analysis: This includes a multi-faceted process:
    - Column Slicing: Eliminating nonessential columns from the database to enhance its efficiency and relevance.
    - Genre and Year Addition: Generate columns denoting the genre and the year of distribution in the database for further analyses.
    - Total Gross Column Preprocessing: Conduct initial adjustment on the "total gross" and "theater sale" column to prepare it for analytical procedures.
    
Within this research project, the following subjects will be inspected:
- Inflation Impact on Movie Rankings: An investigation into whether the ranking of movies in terms of ticket sales remains consistent when altered by inflation.
- Yearly Genre Trends: The identification of the most monemaking genres within each year of analysis.
- Distributor Profit Analysis: An examination of distributors to ascertain those entities that have gathered the highest profits.
- Sentiment Analysis: Using sentiment analysis techniques to evaluate movie titles and subsequently comparing this sentiment analysis with that of the respective movie genres.
- Genre Explorer: Determine the genre of "Unknown" movies in the data frame based on their titles.

## 1.3. Data

### 1.3.1. Data requirments

Our objective need the establishment of a database encompassing annual top-grossing films, their total sale, and their respective genres. Our database mainly relies on box office ticket sales as the primary metric for evaluating a movie's success. This approach is required by the potential manipulation of users' rating on some online platforms, which can be cause by bots, thereby evaluating the integrity of a movie's overall rating is essential.
The logic for using box office ticket sales data is in its reliability as a quantitative measure of a film's success.

### 1.3.2. Choice of database

Our chosen data extraction source is the Box Office Mojo website (https://www.boxofficemojo.com/). This platform serves as a valuable resource, providing access to a diverse range of essential data in the film industry. The data obtained from this website includes critical details such as movie titles, gross revenue, theater earnings, cumulative total revenue, release dates, and film distributors. It is important to note that our data collection specifically focuses on the domestic box office figures for each year. This focus requires selecting the top 200 movies annually, ranked by their domestic total gross. Therefore, it is essential to acknowledge that our dataset does not contain all films released during each year.

"Box Office Mojo is the leading online box office reporting and analysis service that tracks box office receipts both domestically and internationally. Box Office Mojo is a resource for entertainment industry professionals, journalists, researchers, financiers, and movie fans worldwide"(Box Office Mojo website). "While there are other sites that provide detailed box office tracking and a handful that provide a resource for eventual totals, Box Office Mojo was, and is, widely regarded as one of the most reliable box office trackers out there"(Screen Rant website).

The Box Office Mojo website does not provide information regarding the genres of the films. Therefore, to supply our dataset with this information, we are using an additional dataset from Kaggle (accessible at: https://www.kaggle.com/datasets/ashpalsingh1525/imdb-movies-dataset). This additional dataset is extracted from the IMDb platform, which is universally recognized as an essential source for movie-related, television, and celebrity content. The score of 100% in every section (Completeness, Credibility and Compatibility) is given by Kaggle to this dataset.

As the value of US dollar is also effected by inflation threw each yaer, an inflation factor will be identified and use to normalize our coparison. This factor is extracted from  https://www.in2013dollars.com/. It is noted that "Raw data for these calculations comes from the Bureau of Labor Statistics' Consumer Price Index (CPI), established in 1913. Price index data from 1774 to 1912 is sourced from a historical study conducted by political science professor Robert Sahr at Oregon State University and from the American Antiquarian Society. Price index data from 1634 to 1773 is from the American Antiquarian Society, using British pound equivalents" in the website.

### 1.3.3. Other possible databases and limitations

Other websites in the film industry are either unusable or insignificant for our purposes. Examples of them are as follows:

- The-Numbers.com (https://the-numbers.com/):
   The-Numbers.com could be an acceptable source for the specific output we require; however, the limitations hinder our ability to extract data from it via web scraping. This limitation primarily derives from the website's policies, which expressly prohibit the automated harvesting of data as mentioned: "In instances of automated scraping, users will be blocked and investigated" (The-numbers website). 
- Rotten Tomatoes (https://www.rottentomatoes.com/):
   While Rotten Tomatoes offers a wide selection of movies, it does not provide information about the total profit or tickets sell by the featured movies. Lack of financial data, and especially profit, causes Rotten Tomatoes improper for our research needs.

### 1.3.4 Saving the Data Frame

The collected data in section 2 of this notebook is stored after the proper modifications. Therefore, it is possible to start this notebook from part 3 "Analyzing the data" section by importing our saved files. This approache is used to protect the collected data frame against potential changes in online data or server disruptions from our primary data source, we will extract and store each data frame on our own machine to avoid any potential loss.
    
## 1.4. Moral considerations

### 1.4.1. Box office mojo laws

Box Office Mojo's policies do not expressly describe any prohibitions concerning web scraping. It is necessary for individuals engaging in personal utilization or copying of the source data obtained from this platform to check the extant terms and conditions of the website, whilst also ensuring permissions.

### 1.4.2. IMDB dataset from Kaggle

Refer to the main page of the dataset: "This data can be used for various analyses, such as identifying trends in movie genres, exploring the relationship between budget and revenue, and predicting the success of future movies"(IMDB movies dataset, Kaggle).

### 1.4.3. Inflation Calculator

Based on the website (http://www.in2013dollars.com) "Official Data is a website based in San Mateo, California that seeks to collect and process government data for the benefit of the public. Our vision is for technology to enable citizens to understand their government and make important life decisions based on facts.From the economy to transportation to space policy, we're dedicated to making government information open and accessible to the public. Thank you for your support."

### 1.4.3. Impact of analysis

In the context of this project, the primary emphasis is on the analysis of data without attempting to declare the superiority of one genre over another. It is relevant to underscore that these data should be interpreted with due consideration of their limitations, particularly in relation to the total number of cinematic productions in the entire globe.

## 1.5. Coding style

Each cell within this environment of Jupyter Notebook can run independently which contrasts with source-code editors, such as Visual Studio Code (VS Code), where I typically import all necessary libraries at the beginning. In this Jupyter Notebook, I have adopted a different approach by importing libraries as they become relevant. Furthermore, I intend to provide the data both before and after the execution of certain functions to provide a comparative analysis of the changes.
