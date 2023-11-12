---
title: "Conversations with ChatGPT - Machine Learning"
date: 2023-05-26T18:25:09-05:00
draft: false

weight: 100

cover:
  image: "images/ChatGPT_logo.png"
  Alt: ChatGPT
  imageWidth: 300
  imageHeight: 300

tags: ["ML"]
categories: ["ChatGPT"]
---

As a Technical Consultant, I have successfully implemented software solutions using various programming languages, frameworks, and patterns across different platforms throughout my career. The emergence of Google has significantly enhanced my productivity, and I have always admired the knowledgeable community at Stackflow. There, I found individuals who had encountered obstacles before me and others who possessed the solutions. And now, with the advent of Generative AI, a whole new level of innovation has arrived.

Generative AI is a disruptive technology that evokes both awe and apprehension. It has the potential to revolutionize numerous professions, and as a Machine Learning engineer, I was curious to explore its capabilities. Currently, I am enrolled in an "Applied Data Science and Machine Learning" bootcamp, aiming to discover the impact of Generative AI firsthand. It took me approximately six months to acquire proficiency in Python programming and Machine Learning techniques. To challenge myself further, I sought to explore a topic completely unfamiliar to me, something that hadn't been covered in the course and hadn't been searched on Google yet. Through an NPR segment, I came across Sentiment Analysis.

During my exploration of Generative AI, I put it to the test by asking ChatGPT just two questions. Astonishingly, within a mere two minutes, it provided me with an answer. This experience left me truly amazed.

### Question 1

You are a data scientist performing Sentiment analysis. I have a customer satisfaction problem. I want to know, why customers are dissatisfied with my products in the Computers category. You need to read comments and tell me if .. 1) Product is high priced 2) Issue with product quality 3) unhappy with delivery. What deep learning algorithm should I use to solve this problem

> For the customer satisfaction problem in the Computers category, where you want to identify the reasons for customer dissatisfaction based on comments, sentiment analysis can be an effective approach. Specifically, you can use a deep learning algorithm called a Recurrent Neural Network (RNN) with Long Short-Term Memory (LSTM) cells.
>
> LSTM-based RNNs are well-suited for analyzing sequential data, such as sentences or comments, because they can capture the dependencies and long-term relationships between words. This makes them effective for sentiment analysis tasks where the order of words and their context is important.

### Question 2

Let's use Recurrent Neural Network (RNN) with Long Short-Term Memory (LSTM) cells. The data is in a file that's in Parquet format. It has customer_id, product_id and comments. Give me python machine learning code that implement this alogorithm: 1) That finds the best parameters to use and then use the best parameters to build a model that I can use in my production environment

> Certainly! To implement the RNN with LSTM cells for sentiment analysis using customer comments, and to find the best parameters for your model, you can follow the code example provided below. This example assumes you have the necessary libraries such as pandas, scikit-learn, TensorFlow, and Keras installed.

    import pandas as pd
    import numpy as np
    from sklearn.model_selection import train_test_split
    from sklearn.metrics import accuracy_score
    from sklearn.model_selection import GridSearchCV
    from tensorflow.keras.preprocessing.text import Tokenizer
    from tensorflow.keras.preprocessing.sequence import pad_sequences
    from tensorflow.keras.models import Sequential
    from tensorflow.keras.layers import Embedding, LSTM, Dense

    # Load the data from the Parquet file
    df = pd.read_parquet("data.parquet")

    # Split the data into input features (comments) and target variable (reason for dissatisfaction)
    X = df["comments"].values
    y = df["dissatisfaction_reason"].values

    # Split the data into training and testing sets
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

    # Tokenize the input text and convert it to sequences
    tokenizer = Tokenizer()
    tokenizer.fit_on_texts(X_train)
    X_train_seq = tokenizer.texts_to_sequences(X_train)
    X_test_seq = tokenizer.texts_to_sequences(X_test)

    # Pad the sequences to ensure they have the same length
    max_sequence_length = max([len(seq) for seq in X_train_seq])
    X_train_padded = pad_sequences(X_train_seq, maxlen=max_sequence_length)
    X_test_padded = pad_sequences(X_test_seq, maxlen=max_sequence_length)

    # Define the LSTM model
    model = Sequential()
    model.add(Embedding(input_dim=len(tokenizer.word_index) + 1, output_dim=100, input_length=max_sequence_length))
    model.add(LSTM(units=128, dropout=0.2, recurrent_dropout=0.2))
    model.add(Dense(units=3, activation='softmax'))

    # Compile the model
    model.compile(loss='sparse_categorical_crossentropy', optimizer='adam', metrics=['accuracy'])

    # Define the parameter grid for grid search
    param_grid = {
        'units': [64, 128, 256],
        'dropout': [0.2, 0.3, 0.4],
        'recurrent_dropout': [0.2, 0.3, 0.4]
    }

    # Perform grid search to find the best parameters
    grid_search = GridSearchCV(estimator=model, param_grid=param_grid, cv=3)
    grid_search.fit(X_train_padded, y_train)

    # Get the best parameters
    best_params = grid_search.best_params_
    print("Best Parameters:", best_params)

    # Build the final model using the best parameters
    final_model = Sequential()
    final_model.add(Embedding(input_dim=len(tokenizer.word_index) + 1, output_dim=100, input_length=max_sequence_length))
    final_model.add(LSTM(units=best_params['units'], dropout=best_params['dropout'], recurrent_dropout=best_params['recurrent_dropout']))
    final_model.add(Dense(units=3, activation='softmax'))
    final_model.compile(loss='sparse_categorical_crossentropy', optimizer='adam', metrics=['accuracy'])

    # Train the final model using the best parameters
    final_model.fit(X_train_padded, y_train, epochs=10, batch_size=32)

    # Evaluate the final model on the test set
    y_pred = final_model.predict_classes(X_test_padded)
    accuracy = accuracy_score(y_test, y_pred)
    print("Accuracy:", accuracy)

    # Save the final model for use in the product environment
    final_model.save("sentiment_analysis_model.h5")

### Final Thoughts

Truly amazing! Prior to ChatGPT, we used to rely on code snippets that we copied and customized for our specific implementation. However, now we have the ability to obtain pre-customized programs that are ready to run. The next step is to construct a pipeline and execute the code.

Taking it a step further, software developers can piece together individual components like puzzles and create a comprehensive final solution.
