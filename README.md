# Automobile Failure Detection Model

## Overview

In the rapidly evolving world of transportation, the need for efficient and reliable vehicle management has become paramount. This project explores the application of machine learning techniques to predict vehicle failures, offering the potential to enhance automotive safety, reduce maintenance costs, and optimize fleet operations.

By leveraging the **AI4I 2020 Predictive Maintenance Dataset**, this model aims to detect potential failures in vehicles based on various sensor inputs, helping organizations and individuals implement predictive maintenance strategies.

## Dataset

The dataset used in this project is the **[AI4I 2020 Predictive Maintenance Dataset](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset)**, which includes key sensor data related to vehicle performance. This dataset contains a range of attributes including:

- **UDI**: Unique identifier
- **Product ID**: Identifier of the manufactured product
- **Type**: Product type (H/M/L)
- **Air Temperature [K]**
- **Process Temperature [K]**
- **Rotational Speed [rpm]**
- **Torque [Nm]**
- **Tool Wear [min]**
- **Target**: Machine failure status (failure or non-failure)

## Correlation Matrix

This correlation matrix provides insights into how different features of the dataset are related to each other, guiding feature selection and model development.

![Correlation Matrix](https://github.com/user-attachments/assets/a0cb98d3-3343-4197-8d18-f1c12595fa11)

## Performance Metrics

The model's performance was evaluated using various metrics, including accuracy, precision, recall, and F1-score. These metrics offer a comprehensive view of the model’s effectiveness in detecting vehicle failures.

![Performance Metrics](https://github.com/user-attachments/assets/7282edfe-f7da-4f9a-bc84-3e63d871a889)

## Bar Chart of Performance Metrics

This bar chart provides a visual representation of the model's performance across different metrics, highlighting its strengths and potential areas for improvement.

![Performance Metrics Bar Chart](https://github.com/user-attachments/assets/95208ef8-a3cb-402a-85c0-c17ec263c4f1)

## Conclusion

This vehicle failure detection model represents a step forward in utilizing machine learning for predictive maintenance. By identifying potential failures before they occur, this model helps to improve operational efficiency, reduce downtime, and ensure the safety and reliability of vehicles.

## Future Work

Future iterations of this project may explore:

- Integration of more advanced algorithms like deep learning.
- Experimentation with real-time sensor data.
- Expansion of the dataset to cover a broader range of vehicle types and conditions.

## How to Run

1. Clone this repository.
2. Install the required dependencies listed in the `requirements.txt`.
3. Run the model using the command:
   
```bash
   python vehicle_failure_detection.py
