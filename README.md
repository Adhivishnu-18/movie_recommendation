# movie_recommendation
#A movie recommender system project based on content based filtering

import numpy as np
import pandas as pd
import difflib
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity

#loading the data from csv file to a pandas dataframe

movies_data =  pd.read_csv("/content/movies.csv")

#printing first 5 rows of th data set
movies_data.head()

# number of rows and columns in the data frame

movies_data.shape

# selecting the relevent features for recommendation

selected_features = ['genres','keywords','cast','director','tagline']
print(selected_features)

# replacing the null values with null string
for feature in selected_features:
    movies_data[feature]= movies_data[feature].fillna('')

#combining all the selected features
combined_features = movies_data['genres']+' '+movies_data['keywords']+' '+movies_data['tagline']+' '+movies_data['cast']+' '+movies_data['director']

# coverting text data to feature vectors

vectorizer = TfidfVectorizer()
feature_vectors = vectorizer.fit_transform(combined_features)
print(feature_vectors)
#getting the similarity scores using cosine similarity rule
similarity = cosine_similarity(feature_vectors)
print(similarity)
print(similarity.shape)
#getting the user name from the user

movie_name = input(' Enter your favourite movie name : ')

#creating a list of all movies  given in the dataset

list_of_all_titles = movies_data['title'].tolist()

print(list_of_all_titles)
#find close match
find_close_match = difflib.get_close_matches(movie_name,list_of_all_titles)
print(find_close_match)
close_match = find_close_match[0]
print(close_match)
#finding the index of the movie with the title
index_of_the_movie = movies_data[movies_data.title == close_match]['index'].values[0]
print(index_of_the_movie)
similarity_score = list(enumerate(similarity[index_of_the_movie]))
print(similarity_score)
len(similarity_score)
# sorting the movies based on theirsimilarites

sorted_similar_movies = sorted(similarity_score,key = lambda x:x[1],reverse=True)
print(sorted_similar_movies)
#print the name of similar movies based on their index
print("Movies suggested for you : \n")

i=1
for movie in sorted_similar_movies :
  index = movie[0]
  title_from_index = movies_data[movies_data.index==index]['title'].values[0]
  if(i<10):
    print(i,'.',title_from_index)
    i+=1

movie_name = input(' Enter your favourite movie name : ')

list_of_all_titles = movies_data['title'].tolist()

find_close_match = difflib.get_close_matches(movie_name,list_of_all_titles)

close_match = find_close_match[0]

index_of_the_movie = movies_data[movies_data.title == close_match]['index'].values[0]

similarity_score = list(enumerate(similarity[index_of_the_movie]))

sorted_similar_movies = sorted(similarity_score,key = lambda x:x[1],reverse=True)

print("Movies suggested for you : \n")

i=1
for movie in sorted_similar_movies :
  index = movie[0]
  title_from_index = movies_data[movies_data.index==index]['title'].values[0]
  if(i<10):
    print(i,'.',title_from_index)
    i+=1

