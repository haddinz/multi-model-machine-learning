# Multi-Model Machine Learning Web

This project is a full-stack web application designed to showcase a Multi-Model Machine Learning Web of machine learning models. It features a modern, interactive frontend built with React and a robust backend powered by Python and FastAPI. Users can interact with different models to get predictions based on their input.

## Features

This Multi-Model Machine Learning Web demonstrates three distinct machine learning models:

1.  **Iris Flower Classification**: Utilizes a **Scikit-learn Decision Tree** classifier to predict the species of an Iris flower (`Iris-setosa`, `Iris-versicolor`, `Iris-virginica`) based on its sepal and petal dimensions.
2.  **Diabetes Prediction**: Employs a **Scikit-learn Support Vector Machine (SVM)** to predict the likelihood of diabetes based on several diagnostic measurements.
3.  **Room Cleanliness Classification**: A **Convolutional Neural Network (CNN)** built with TensorFlow/Keras that classifies an uploaded image of a room as either 'clean' or 'messy'.

## Tech Stack

The project is a monorepo with a separate client and server.

**Client (Frontend)**
*   **Framework**: React (with Vite)
*   **Language**: TypeScript
*   **Styling**: Tailwind CSS
*   **Routing**: React Router
*   **Animations**: Framer Motion
*   **API Client**: Axios

**Server (Backend)**
*   **Framework**: FastAPI
*   **Language**: Python
*   **ML Libraries**: Scikit-learn, TensorFlow, Keras
*   **Model Persistence**: Joblib
*   **Web Server**: Uvicorn

## Project Structure

```
.
├── client/         # React frontend application
│   ├── src/
│   │   ├── pages/
│   │   │   ├── models/  # Components for each ML model page
│   │   └── ...
│   └── ...
└── server/         # FastAPI backend
    ├── app/
    │   └── routers/  # API endpoints for each model
    ├── machine_learning/
    │   ├── decision_tree/
    │   │   ├── ml_model.ipynb
    │   │   └── saved_models/model.joblib
    │   ├── sklearn_svm/
    │   │   ├── ml_model.ipynb
    │   │   └── saved_models/model.joblib
    │   └── clasification_room/
    │       ├── ml_model.ipynb
    │       └── saved_models/model.joblib
    └── main.py       # Main application entry point
```

## Getting Started

Follow these instructions to get the project running on your local machine.

### Prerequisites

*   Node.js and npm
*   Python 3.10+ and pip

### 1. Backend Setup

First, set up and run the FastAPI server.

```bash
# Navigate to the server directory
cd server

# Create and activate a virtual environment
# On macOS/Linux:
python3 -m venv env
source env/bin/activate

# On Windows:
python -m venv env
.\env\Scripts\activate

# Install the required Python packages
pip install -r requirements.txt

# Run the FastAPI server
uvicorn app:app --reload --port 4000
```
The backend API will now be running on `http://localhost:4000`.

### 2. Frontend Setup

Next, in a separate terminal, set up and run the React client.

```bash
# Navigate to the client directory
cd client

# Install dependencies
npm install

# Run the development server
npm run dev
```
The frontend application will be accessible at `http://localhost:3000`.

## API Endpoints

The backend provides the following endpoints for model interaction:

*   **Iris Prediction (Decision Tree)**
    *   `POST /api/model/model-iris/post`
    *   **Body:**
        ```json
        {
          "sepalLengthCm": 5.1,
          "sepalWidthCm": 3.5,
          "petalLengthCm": 1.4,
          "petalWidthCm": 0.2
        }
        ```

*   **Diabetes Prediction (SVM)**
    *   `POST /api/model/model-diabetes/post`
    *   **Body:**
        ```json
        {
          "pregnancies": 6,
          "glucose": 148,
          "bloodPressure": 72,
          "skinThickness": 35,
          "insulin": 0,
          "bmi": 33.6,
          "diabetesPedigreeFunction": 0.627,
          "age": 50
        }
        ```

*   **Room Classification (CNN)**
    *   `POST /api/model/clasification_room/post`
    *   **Body:** `multipart/form-data` with a key `image_upload` containing the image file to be classified.
