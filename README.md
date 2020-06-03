# Forecasting COVID-19 Cases Using FB Prophet

#### This is a time series forecasting using FB Prophet aiming to forecast upcoming confirmed and active cases of COVID-19 in worldwide and India.
 
###### note :  
1. Dataset is till 28 may,2020. [Link](https://www.kaggle.com/sudalairajkumar/novel-corona-virus-2019-dataset/ "kaggle.com") to the dataset
2. I have used "Prophet", a time series forecasting library by FB Prophet. [Click here](https://facebook.github.io/prophet/docs/quick_start.html "FB Prophet") to view the documentation.
3. This analysis is for academic purpose and does not intend to spread misinformation. 
4. Predicting data is a well established study in data science and there is always a scope of correction in predicted outcomes.
5. I am not a health professional or epidemiologist, and the analysis done in this notebook should not be interpreted as professional advice. 
---

#### As the focus is on confirmed and active cases worldwide and in India, main dataframe is divided into 4 dataframes 
#
###### 1. world_confirmed

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Confirmed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-01-22</td>
      <td>555.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-01-23</td>
      <td>653.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-01-24</td>
      <td>941.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-01-25</td>
      <td>1438.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-01-26</td>
      <td>2118.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>123</th>
      <td>2020-05-24</td>
      <td>5407613.0</td>
    </tr>
    <tr>
      <th>124</th>
      <td>2020-05-25</td>
      <td>5495061.0</td>
    </tr>
    <tr>
      <th>125</th>
      <td>2020-05-26</td>
      <td>5589626.0</td>
    </tr>
    <tr>
      <th>126</th>
      <td>2020-05-27</td>
      <td>5691790.0</td>
    </tr>
    <tr>
      <th>127</th>
      <td>2020-05-28</td>
      <td>5808946.0</td>
    </tr>
  </tbody>
</table>
<p>128 rows × 2 columns</p>
</div>

---

###### 2. world_active

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Active</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-01-22</td>
      <td>510.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-01-23</td>
      <td>605.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-01-24</td>
      <td>879.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-01-25</td>
      <td>1357.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-01-26</td>
      <td>2010.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>123</th>
      <td>2020-05-24</td>
      <td>2893991.0</td>
    </tr>
    <tr>
      <th>124</th>
      <td>2020-05-25</td>
      <td>2917091.0</td>
    </tr>
    <tr>
      <th>125</th>
      <td>2020-05-26</td>
      <td>2952217.0</td>
    </tr>
    <tr>
      <th>126</th>
      <td>2020-05-27</td>
      <td>2986073.0</td>
    </tr>
    <tr>
      <th>127</th>
      <td>2020-05-28</td>
      <td>3032678.0</td>
    </tr>
  </tbody>
</table>
<p>128 rows × 2 columns</p>
</div>

---
3. india_confirmed

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Confirmed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-01-30</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-01-31</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-02-01</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-02-02</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-02-03</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>115</th>
      <td>2020-05-24</td>
      <td>138536.0</td>
    </tr>
    <tr>
      <th>116</th>
      <td>2020-05-25</td>
      <td>144950.0</td>
    </tr>
    <tr>
      <th>117</th>
      <td>2020-05-26</td>
      <td>150793.0</td>
    </tr>
    <tr>
      <th>118</th>
      <td>2020-05-27</td>
      <td>158086.0</td>
    </tr>
    <tr>
      <th>119</th>
      <td>2020-05-28</td>
      <td>165386.0</td>
    </tr>
  </tbody>
</table>
<p>120 rows × 2 columns</p>
</div>

---

###### 4. india_active

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Active</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2020-01-30</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2020-01-31</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2020-02-01</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2020-02-02</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2020-02-03</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>115</th>
      <td>2020-05-24</td>
      <td>76820.0</td>
    </tr>
    <tr>
      <th>116</th>
      <td>2020-05-25</td>
      <td>80072.0</td>
    </tr>
    <tr>
      <th>117</th>
      <td>2020-05-26</td>
      <td>82172.0</td>
    </tr>
    <tr>
      <th>118</th>
      <td>2020-05-27</td>
      <td>85803.0</td>
    </tr>
    <tr>
      <th>119</th>
      <td>2020-05-28</td>
      <td>89755.0</td>
    </tr>
  </tbody>
</table>
<p>120 rows × 2 columns</p>
</div>

---

#### On each dataframe, following steps are applied :
-  renaming the columns (renaming to 'ds' and 'y')
- building the model
- fitting the model
- creating dataframe for upcoming days
- forecasting
- plotting 

---

---

# In Conclusion 
#### By The End of June, 2020 , There Will Be ^:
    - 8.7 millions of confirmed cases worldwide
    - 4.2 millions of active cases worldwide
    - 308k of confirmed cases in India
    - 158k of active cases in India
    
  ^(actual results may vary)
  
##### Although the outcomes of forecasting may seems disheartening but this is just a prediction, which is based on past data and the actual results are bound to change. If we all follow social distancing and practice basic hygiene, I think we can come with something  far less than the predicted values. 
