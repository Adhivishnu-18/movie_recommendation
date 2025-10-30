

#  Movie Recommendation System

*A Content-Based Filtering Project using Cosine Similarity*

## Overview

This project is a **content-based movie recommender system** that suggests movies similar to a user’s favorite movie. It uses **TF-IDF Vectorization** and **Cosine Similarity** to find and rank movies based on textual features such as *genres*, *keywords*, *cast*, *director*, and *tagline*.

---

## Features

* Recommends movies similar to the one you input.
* Uses **content-based filtering** — no user ratings needed.
* Employs **TF-IDF (Term Frequency – Inverse Document Frequency)** for feature extraction.
* Uses **Cosine Similarity** to measure movie similarity.
* Handles missing data gracefully.

---

## Tech Stack

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn** (for TF-IDF and cosine similarity)
* **Difflib** (for fuzzy string matching)

---

##  Dataset

The dataset used is `movies.csv`, containing details about various movies such as:

* `title`
* `genres`
* `keywords`
* `cast`
* `director`
* `tagline`

*(Ensure your CSV file includes these columns.)*

---

##  How It Works

1. Load the movie dataset using **Pandas**.
2. Select key textual features (`genres`, `keywords`, `cast`, `director`, `tagline`).
3. Replace missing values with empty strings.
4. Combine all selected features into a single text field.
5. Convert the combined text into numerical feature vectors using **TfidfVectorizer**.
6. Compute **cosine similarity** between all movies.
7. Take user input for a favorite movie.
8. Find the closest match for that movie title.
9. Retrieve and display the **top 10 most similar movies**.

---

##  Example Usage

```bash
Enter your favourite movie name : Avatar
```

**Output:**

```
Movies suggested for you :

1. Guardians of the Galaxy  
2. Star Trek  
3. John Carter  
4. The Avengers  
5. The Matrix  
6. The Fifth Element  
7. Interstellar  
8. Star Wars  
9. Thor: Ragnarok  
```

---

##  Concepts Used

* **Content-Based Filtering**: Recommends items similar to what a user likes, based on item attributes.
* **TF-IDF Vectorization**: Converts text into meaningful numerical representations.
* **Cosine Similarity**: Measures similarity between two movie feature vectors.
* **String Matching (Difflib)**: Helps handle user typos or partial matches when entering movie names.

---

##  Setup Instructions

1. Clone the repository or copy the code.
2. Install the required libraries:

   ```bash
   pip install numpy pandas scikit-learn
   ```
3. Place your `movies.csv` file in the same directory.
4. Run the Python file:

   ```bash
   python movie_recommendation.py
   ```
5. Enter your favorite movie name when prompted.

---

## Output

The program displays the top **10 most similar movies** based on cosine similarity scores.

---

##  Future Improvements

* Integrate a **web UI** using Streamlit or Flask.
* Add **collaborative filtering** for hybrid recommendations.
* Include more metadata (e.g., movie overview, release date).
* Optimize with **dimensionality reduction (SVD or PCA)**.

---


