# Clothes Demand Prediction
* Predicting the demand of Clothes using LSTM and 3-layer neural network.
* To run the given codes, install Keras with tensorflow backend in your IPython shell (preferably Anaconda).

**Business Problem**
* Predicting the demand of various Clothing types in order to avoid inventory wastage.
* No input is at disposal, hence the input variables need to be forecasted and then the target variable is regressed through the forecasted input variable

> Data Definition and Understanding
* Input variables
1. AvgSP - Average Selling Price of SKU
2. OP - Average Selling Price of various clothes
3. CustomerCount - Total GT Customers for the given SKU ( = CustomerCount + Missed Customers)
* Target Variable - ActualDemand of SKU ( = Ordered Quantity + Missed Demand)

* Summary Stats

![input_var_summ](https://user-images.githubusercontent.com/26039458/27529278-758c9838-5a71-11e7-836e-73e87002a99e.png)

![ouput_var_summ](https://user-images.githubusercontent.com/26039458/27529276-758ba162-5a71-11e7-8017-f8dc513c4e71.png)

<!-- * Summary Stats on SKU 2

![sums_inp_carr](https://user-images.githubusercontent.com/26039458/27531850-bad1a762-5a7b-11e7-9508-f3e227b3acd1.png)

![sums_out_carr](https://user-images.githubusercontent.com/26039458/27531852-bad347a2-5a7b-11e7-85e6-10ff77aa753b.png)

* Summary Stats on SKU 3

![ridge_inp_summ](https://user-images.githubusercontent.com/26039458/27532825-16325176-5a7f-11e7-8076-102564db7fe5.png)

![ridge_out_sums](https://user-images.githubusercontent.com/26039458/27532823-16322d68-5a7f-11e7-9251-077ce279d933.png)

 -->
> Training and Test Datasets
* The last week of the complete dataset is considered for testing while the rest of the dataset is considered for training

> Function to create Data Input to model
* AvgSP
1. @AvgSP is predicted using time series forecasting.
2. Long Short-Term Memory (Recurrent Neural Network) method is used for forecasting. The forecasting problem is now considered as a supervised learning problem where the input is the value prior to the target day.
3. LSTM is a special type of Neural Network which remembers information across long sequences to facilitate the forecasting.
4. Forecasting results

![avgsp_pred_cucum](https://user-images.githubusercontent.com/26039458/27529407-081dae9e-5a72-11e7-8af3-3f42b35da27c.png)


<!-- * SKU 2 - rmse = Rs. 1.9

![avgsp_pred_carr](https://user-images.githubusercontent.com/26039458/27531797-90d7c9f0-5a7b-11e7-822a-248668a02bc9.png)


* SKU 3 - rmse = Rs. 1.5

![ridge_avgsp](https://user-images.githubusercontent.com/26039458/27532820-15f5a92e-5a7f-11e7-8697-e998fb7f400e.png)
 -->

* CustomerCount
1. @CustomerCount is predicted using the same method as @AvgSP
2. Forecasting Results
<!-- * SKU 1 - 12 Customers
 -->
![cc_pred_cucum](https://user-images.githubusercontent.com/26039458/27529275-75892996-5a71-11e7-876c-4e7c0d03e27a.png)

<!-- * SKU 2 - rmse = 50 Customers

![cc_pred_carr](https://user-images.githubusercontent.com/26039458/27531847-bacc62d4-5a7b-11e7-81e9-d5c5317ee25c.png)


* SKU 3 - rmse = 52 Customers

![ridge_cc_pred](https://user-images.githubusercontent.com/26039458/27532821-162f4a30-5a7f-11e7-8f18-d04b4ce38fe5.png)
 -->
<!-- * Onion Price is known with good accuracy due to information about the lot size. -->

**Data Modelling**
> Model Name
* 3-layer Neural Network using Keras Library (tensorflow backend)
* The network is made up of 3 layers:

1. Input layer
- Takes input variables and converts them into input equation
- Parameters: no. of neurons (memory blocks) = 16, activation function = linear, weight initializer = normal distribution, kernel and activity regularizer = L1 (alpha = 0.1)

2. Hidden Layer
- The processing (optimization) takes place in this layer.
- Parameters: no. of neurons = 8, activation function = linear, weight initializer = normal distribution, kernel and activity regularizer = L1 (alpha = 0.1)

3. Output Layer
- Converts the processed results into a reverse scaled output.

> Model Performance



<!-- 2. SKU 2 - rmse = 250 Kg -->

![train_dem_carr](https://user-images.githubusercontent.com/26039458/27531849-bad1b22a-5a7b-11e7-9d43-2318f459241a.png)

![dem_pred_carr](https://user-images.githubusercontent.com/26039458/27531851-bad230ec-5a7b-11e7-84b4-1bbb30d613f9.png)

![carr_dem_fore](https://user-images.githubusercontent.com/26039458/27531848-bacf5958-5a7b-11e7-940c-438f79285683.png)

