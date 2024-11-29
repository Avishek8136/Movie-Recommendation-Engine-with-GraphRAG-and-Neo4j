# **Movie Recommendation Engine: GraphRAG Architecture**

Welcome to the **Movie Recommendation Engine** project! This project demonstrates how to design a movie recommendation system using a **GraphRAG architecture** to identify and suggest similar movies based on their attributes and relationships.

---

## **Problem Statement**

In an era where movies are produced in large numbers, finding similar movies based on a user's preferences has become a challenging task. Imagine a user watches the movie **“3 Idiots”** and wants recommendations for similar films. The goal of this project is to design a recommendation engine that suggests the **next three most similar movies** based on various factors, such as:

* Plot similarity
* Actor and director overlap
* Year of release
* Audience votes

---

## **Solution Overview**

This project leverages:

* **Graph Databases** : Using Neo4j to model movies as nodes and similarities as relationships (`SIMILAR_TO`).
* **Text Analysis** : Using TF-IDF and cosine similarity to measure plot similarity.
* **Feature Engineering** : Calculating scaled similarities for actors, directors, votes, and year of release.
* **Weighted Scoring** : Combining multiple similarity metrics to create a robust recommendation engine.

---

## **Features**

1. **Movie Similarity Calculation** : Computes a composite similarity score for movies.
2. **Graph-Based Recommendations** : Utilizes Neo4j to create relationships and fetch recommendations.
3. **Weighted Similarity** :

* Plot: 40%
* Actors/Directors: 30%
* Year: 20%
* Votes: 10%

1. **Customizable Thresholds** : Configure the similarity threshold for defining relationships.

---

## **Prerequisites**

1. **Python** : Version 3.8 or above.
2. **Neo4j** : Community edition or higher (local or cloud instance).
3. **Libraries** : Install the following Python libraries:

```bash
   pip install pandas numpy scikit-learn py2neo
```

---

## **Dataset**

The dataset used is sourced from Kaggle:  **[Bollywood Dataset (10,000 Movies)](https://www.kaggle.com/datasets/mustafaanandwala/10000-bollywood-dataset)** .

The dataset includes:

* Movie names
* Plot descriptions
* IMDb ratings
* Vote counts
* Year of release
* Directors and actors

---

## **How It Works**

### **Step 1: Data Preprocessing**

* Remove duplicates and handle missing values.
* Normalize numerical data (votes and year of release).
* Vectorize plot descriptions using  **TF-IDF** .
* Extract actors and directors for similarity calculations.

### **Step 2: Graph Database Setup**

* Movies are added as **nodes** in Neo4j.
* Relationships (`SIMILAR_TO`) are created between movies with similarity scores above a threshold (e.g., 0.5).

### **Step 3: Composite Similarity Calculation**

* Compute:
  * Plot similarity using cosine similarity.
  * Actor/Director overlap as a percentage.
  * Scaled differences for year and vote counts.
* Combine these metrics using weighted scoring.

### **Step 4: Query Recommendations**

* Use Cypher queries in Neo4j to retrieve the top 3 similar movies for a given input movie.

---

## **How to Run**

### **1. Set Up Neo4j**

1. Install Neo4j and start the database server.
2. Create a database and note the credentials (`username`, `password`).
3. Update the Python script with your Neo4j credentials.

### **2. Run the Python Script**

1. Clone this repository and navigate to the project directory:
   ```bash
   git clone https://github.com/Avishek8136/Movie-Recommendation-Engine-with-GraphRAG-and-Neo4j
   cd movie-recommendation-engine
   ```
2. Ensure the dataset (`bollywood_data_set.csv`) is in the same directory.
3. Run the script:
   ```bash
   python recommendation_engine.py
   ```

### **3. Test the Recommendation System**

* Query the system for recommendations:
  ```bash
  python
  from recommendation_engine import recommend_movies
  print(recommend_movies("3 Idiots"))
  ```

## **Outputs**

* Top 3 recommended movies based on similarity, along with their ratings and votes.

Example for  **"3 Idiots"** :

```plaintext
Recommendations:
1. "Taare Zameen Par" (Rating: 8.4, Votes: 92,000)
2. "Chhichhore" (Rating: 8.3, Votes: 76,000)
3. "PK" (Rating: 8.2, Votes: 120,000)
```

---

## **Project Structure**

```
📁 movie-recommendation-engine
├── bollywood_data_set.csv         # Input dataset
├── recommendation_engine.ipynb    # Jupyter Notebook for recommendation system
├── README.md                      # Documentation
├── architecture_slide.pdf         # Model architecture diagram
├── demo_video.mp4                 # Demo video (walkthrough of solution)
├── requirements.txt               # Required Python Libraries
```

---

## **Model Architecture**

Refer to the **`architecture_slide.pdf`** for a visual representation of the workflow. It includes:

1. **Data Input** : Bollywood dataset.
2. **Processing Layer** : Data cleaning, TF-IDF vectorization, and feature engineering.
3. **Graph Database** : Movies as nodes, similarities as edges.
4. **Recommendation Layer** : Query Neo4j for similar movies.

---

## **Demo Video**

Watch the demo video (`demo_video.mp4`) for a step-by-step walkthrough of:

1. Problem statement and approach.
2. Code structure and functionality.
3. Example queries and recommendations.

<iframe width="560" height="315" src="https://www.youtube.com/embed/3LPhSc2ukEk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


---

## **Contact**

For any questions or feedback, feel free to reach out via GitHub or email at avishekrauniyar07@gmail.com.

Happy coding! 🎥🎬
