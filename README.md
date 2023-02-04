# Crime_prediction

To begin with, we simplified the task a bit and tried to predict the number of crimes. First we used LSTM (found in BaseLine).

We did a literature review and realized that time series models were needed. Took prophet, also considered ARIMA.

We figured out the Prophet documentation and wrote a code that predicts the frequency of crimes in a time series. Added crimes(holidays) as events for prophet-a

Dataset: https://data.world/kylesykes/st-louis-city-crime-data

Model: prophet

Further plans: the fact is that prophet accepts ds and y. ds -- date, y -- target. Now the number of crimes for the current date is taken as the target, crimes are added to it as events. However, the model will learn to predict the number of crimes in the future. We do not want this, we want the type, time and place. To fix this, it is proposed to pass a one_hot vector (one there, what type of crime happened). However, you still need to bind the place to this vector. It is proposed to make another one-hot vector for the location and concatenate it with the first one.

How it will work: time will be given as input (you can simply do future = model.make_future_dataframe(periods = 365)), at the output we will get a vector from which it will be possible to get information about the place and type of crime.
