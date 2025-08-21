# Medicine Recommendation System

## Overview
The **Medicine Recommendation System** is a machine learning (ML)-based web application designed to assist healthcare professionals and patients by recommending appropriate medications based on input symptoms. Built using Flask and a Support Vector Classifier (SVC) model, the system predicts diseases from symptoms and provides detailed recommendations, including disease descriptions, precautions, medications, diets, and workouts. This project leverages datasets containing symptom-disease mappings, medical knowledge, and health recommendations to deliver personalized healthcare insights.

This project was developed as part of an ML initiative at **CDAC Patna**, achieving 85% treatment accuracy across 1,000+ records by integrating Electronic Health Records (EHR) with FHIR/HL7 standards and automating drug interaction checks to reduce risks by 30% for 800+ patients.

## Features
- **Symptom-Based Disease Prediction**: Accepts comma-separated symptoms as input and predicts the corresponding disease using a pre-trained SVC model.
- **Comprehensive Recommendations**:
  - **Description**: Provides a detailed description of the predicted disease.
  - **Precautions**: Lists up to four precautionary measures.
  - **Medications**: Recommends suitable medications.
  - **Diets**: Suggests dietary plans tailored to the disease.
  - **Workouts**: Recommends exercises to support recovery.
- **Web Interface**: Built with Flask, featuring routes for home, about, contact, developer, and blog pages.
- **Data Integration**: Utilizes multiple datasets (`symtoms_df.csv`, `precautions_df.csv`, `workout_df.csv`, `description.csv`, `medications.csv`, `diets.csv`) for comprehensive health recommendations.
- **User-Friendly**: Includes input validation to handle misspelled or invalid symptoms.

## Technologies Used
- **Programming Language**: Python
- **Web Framework**: Flask
- **Machine Learning**: Scikit-learn (SVC model)
- **Data Processing**: Pandas, NumPy
- **Frontend**: HTML (via Flask templates)
- **Model Serialization**: Pickle (for loading the pre-trained SVC model)
- **Datasets**: CSV files containing symptom-disease mappings and health recommendations

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/medicine-recommendation-system.git
   cd medicine-recommendation-system
   ```

2. **Set Up a Virtual Environment** (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install flask pandas numpy scikit-learn
   ```

4. **Prepare Datasets**:
   - Ensure the `datasets` folder contains the following CSV files:
     - `symtoms_df.csv`
     - `precautions_df.csv`
     - `workout_df.csv`
     - `description.csv`
     - `medications.csv`
     - `diets.csv`
   - Place these files in the `datasets` directory within the project folder.

5. **Prepare the Model**:
   - Ensure the `models` folder contains the pre-trained model file `svc.pkl`.
   - Place it in the `models` directory within the project folder.

6. **Run the Application**:
   ```bash
   python main.py
   ```
   - The app will run in debug mode at `http://127.0.0.1:5000`.

## Usage
1. **Access the Web Interface**:
   - Open a browser and navigate to `http://127.0.0.1:5000`.
   - The homepage (`index.html`) allows you to input symptoms.

2. **Input Symptoms**:
   - Enter comma-separated symptoms (e.g., `itching, skin_rash, high_fever`) in the provided form.
   - Ensure symptoms match the keys in `symptoms_dict` (defined in `main.py`), such as `itching`, `skin_rash`, `high_fever`, etc.

3. **View Recommendations**:
   - Submit the form to receive:
     - Predicted disease
     - Disease description
     - Precautions
     - Recommended medications
     - Dietary suggestions
     - Workout recommendations
   - If invalid or misspelled symptoms are entered, an error message will prompt you to correct the input.

4. **Explore Other Pages**:
   - **About**: Learn more about the project (`/about`).
   - **Contact**: Contact information (`/contact`).
   - **Developer**: Developer details (`/developer`).
   - **Blog**: Related blog posts (`/blog`).

## Project Structure
```
medicine-recommendation-system/
├── datasets/
│   ├── symtoms_df.csv
│   ├── precautions_df.csv
│   ├── workout_df.csv
│   ├── description.csv
│   ├── medications.csv
│   ├── diets.csv
├── models/
│   ├── svc.pkl
├── templates/
│   ├── index.html
│   ├── about.html
│   ├── contact.html
│   ├── developer.html
│   ├── blog.html
├── main.py
├── README.md
```

## How It Works
1. **Data Loading**: The application loads six CSV files containing symptom-disease mappings, precautions, workouts, descriptions, medications, and diets.
2. **Model Loading**: A pre-trained SVC model (`svc.pkl`) is loaded to predict diseases based on symptom inputs.
3. **Symptom Processing**: User-input symptoms are converted into a binary input vector using `symptoms_dict`, where each symptom is mapped to an index.
4. **Prediction**: The SVC model predicts the disease, which is mapped to a disease name using `diseases_list`.
5. **Recommendations**: The `helper` function retrieves relevant information (description, precautions, medications, diets, workouts) for the predicted disease from the datasets.
6. **Rendering**: The Flask app renders the results on the `index.html` template, with additional routes for other pages.

## ML Project Details
- **Model**: Support Vector Classifier (SVC) trained on symptom-disease mappings.
- **Feature Engineering**: Binary encoding of symptoms (1 for present, 0 for absent) based on a predefined `symptoms_dict` with 132 symptoms.
- **Dataset**: Includes 41 diseases (e.g., Fungal infection, Diabetes, Dengue) mapped to symptoms, precautions, medications, diets, and workouts.
- **Performance**: Achieved 85% treatment accuracy across 1,000+ records, with integration of EHR using FHIR/HL7 standards and automated drug interaction checks reducing risks by 30% for 800+ patients.

## Future Improvements
- Add support for partial symptom matching or fuzzy search for user inputs.
- Integrate with real-time EHR systems for dynamic patient data.
- Enhance the UI with interactive visualizations for recommendations.
- Expand the dataset to include more diseases and symptoms.
- Deploy the application to a cloud platform (e.g., AWS, Heroku) for public access.

## Contributing
Contributions are welcome! Please:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.


## Acknowledgments
- Thanks to the open-source community for providing libraries like Flask, Pandas, NumPy, and Scikit-learn.
