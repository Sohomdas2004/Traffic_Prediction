Traffic Situation Prediction 🚦

This project uses machine learning to predict traffic situations (e.g., low, normal, high, heavy) based on vehicle counts, time, and day of the week. The dataset (Traffic.csv) contains traffic counts recorded at 15-minute intervals.

📂 Dataset

The dataset has the following columns:

Time – Time of the record (HH:MM AM/PM format)

Date – Day of the month (integer)

Day of the week – Categorical (Monday, Tuesday, …)

CarCount – Number of cars

BikeCount – Number of bikes

BusCount – Number of buses

TruckCount – Number of trucks

Total – Total vehicles

Traffic Situation – Target variable (low / normal / high / heavy)

⚙️ Steps in the Notebook

Load the dataset (Traffic.csv)

Feature Engineering

Convert Time into Hour and Minute

Encode Day of the week into numeric values

Preprocessing

Prepare features (X) including vehicle counts, time, and day

Encode target (Traffic Situation) with LabelEncoder

Train/Test Split – 80/20 split

Model Training

Use a RandomForestClassifier

Evaluation

Print accuracy and classification report

Achieved ~99.8% accuracy

Prediction on New Data

Example: Car=50, Bike=10, Bus=5, Truck=2, Time=9:30 AM, Monday

Predicts the traffic situation (e.g., normal)

📊 Example Prediction
example = {
    'CarCount': 50,
    'BikeCount': 10,
    'BusCount': 5,
    'TruckCount': 2,
    'Total': 67,
    'Hour': 9,
    'Minute': 30,
    'DayEncoded': day_encoder.transform(['Monday'])[0]
}
example_df = pd.DataFrame([example])
pred = model.predict(example_df)
pred_label = target_encoder.inverse_transform(pred)
print("Predicted Traffic Situation:", pred_label[0])


Output:

Predicted Traffic Situation: normal

🚀 How to Use

Open the Colab notebook.

Upload the Traffic.csv file.

Run all cells to train and evaluate the model.

Modify the example input section to test with your own vehicle counts and time.
