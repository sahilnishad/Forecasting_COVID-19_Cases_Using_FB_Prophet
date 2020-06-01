# Forecasting COVID-19 Cases Using FB Prophet

#### This is a time series forecasting using FB Prophet aiming to forecast upcoming confirmed and active cases of COVID-19 in worldwide and India.
 
###### note :  
1. Dataset is till 28 may,2020. [Link](https://www.kaggle.com/sudalairajkumar/novel-corona-virus-2019-dataset/ "kaggle.com") to the dataset
2. I have used "Prophet", a time series forecasting library by FB Prophet. [Click here](https://facebook.github.io/prophet/docs/quick_start.html "FB Prophet") to view the documentation.
3. This analysis is for academic purpose and does not intend to spread misinformation. 
4. Predicting data is a well established study in data science and there is always a scope of correction in predicted outcomes.
5. I am not a health professional or epidemiologist, and the analysis done in this notebook should not be interpreted as professional advice. 


#### I Have followed 6 steps to forecast each dataframe :
-  renaming the columns (renaming to 'ds' and 'y')
- building the model
- fitting the model
- creating dataframe for upcoming days
- forecasting
- plotting 

# In Conclusion 
#### By The End of June, 2020 , There Will Be ^:
    - 8.7 millions of confirmed cases worldwide
    - 4.2 millions of active cases worldwide
    - 308k of confirmed cases in India
    - 158k of active cases in India
    
  ^(actual results may vary)
  
###### Although the outcomes of forecasting may seems disheartening but this is just a prediction, which is based on past data and the actual results are bound to change. If we all follow social distancing and practice basic hygiene, I think we can come with something  far less than the predicted values. 
