# Will the customer accept the coupon

### Problem Statemewnt

Ultimately, I would like to increase business for my client who has a mid-priced ($20 - $50 / person) restaurant.  I am proposing to my client that we distribute coupons in order to increase their business.  In order to do so, I would like to determine the best way to distribute coupons for mid-priced restaurants in general. 

I will look at who will accept the coupons, where they will accept them, and when they will accept them.

I am assuming that the distribution of coupons to those who will not accept them will only make them less likely to accept them at a future date, because they occur as spam.  Therefore, I only want to distribute coupons when they are likely to be accepted.

### Data Cleaning

There are missing values in the car, Bar, CoffeeHouse, CarryAway, RestaurantLessThan20, and Restaurant20To50 columns.

There are not many values in the car column, therefore, this might not be a useful column.  The data in this column seems to be the type of car.  However, it doesn't look like it was collected consistently.  Because of the lack of data and data consistency, I decided to drop the car column.

The other columns with missing data only have a few items missing.  However, all of these columns have 'never' as a possible value.  It is probably safe to assume that respondents did not answer some questions when it did not apply to them. Therefore, I decided to fill these missing values with 'never'.

### Analysis

Analysis of the coupon type distribution reveals that there are only 1492 coupons for mid-priced restaurants.  This is the least of any coupon type, so it could make this analysis a bit difficult.  However, it is over 1000 coupons, so we should be able to see some trends.

I looked at the overall mid-priced coupon acceptance rate, so that I could use this as a baseline.  This acceptance rate is 44.1% for 1492 people.  

I then, in an automated fashion, computed the acceptance rate for each unique value for each column of catagorical data.  I initially looked at which values had an acceptance rate at least 10 points greater than the rejection rate.  For further analysis, I only considered the subset of those columns with these values that increased the coupon acceptance.  I plotted bar graphs for the coupon acceptance rates for all values in these columns and colored the bars in the following manner: green for bars with > 50% acceptance rate, red for bards with < 40 % acceptance rate, and red for all bars in the 40 - 50% acceptance rates.


#### EDA

The following bar graphs show the coupon acceptance rates for the unique values in those columns which significantly impact the coupon acceptance rates:
![alt text](images/Mid-priced%20restaurant%20coupon%20acceptance%20drivers.png)

Some of these categories are not as prevalent as others.  In order to determine the what might be data limited, the distribution of these categories was plotted:
![alt text](images/Mid-priced%20restaurant%20coupon%20acceptance%20driver%20distributions.png)


### Results

#### The following are positively correlated to coupon acceptance:

The frequency of going to a mid-priced restaurant is strongly correlated to the acceptance rate of this type of coupon.
    (68.8%, 62.6%, 52.7%, and 29.8% acceptance rate for those who go to mid-priced restaurants > 8 times/mo, 4-8 times, 1-3 times, and never.)
Therefore, distributing coupons to those who are at a resturant might be a good way to get these customers to come back more frequently.

The following occupations tend to accept coupons more than others:  
   Healthcare Support (65.6%), 
   Construction & Extraction (61.9%), 
   Office & Administrative Support (61.5%), 
   Production Occupations (61.5%)
Therefore, it may be worthwhile to distribute coupons at hospitals, medical clinics, contractor supply houses, and office buildings.

In general, those with some high school (58.3%) or high school graduates (51.9%) have a higher acceptance rate that those with more education.  
I am not certain how but there may be a way to target these people.

The time of day appears to make a difference with reguards to mid-priced restaurant coupon acceptance.
The best times are at 10AM (61.6%) and 2PM (53.8%).  However, there is a strong negative correlation with 10PM.
Therefore, it may be best to distribute coupons to the aforementioned business as people are about to head out to lunch or home for the day.

Being sunny does not appear to drive coupon acceptance.  However, not being sunny appears to negatively impact coupon acceptance (29.9%).
Therefore, one may only want to pay to distribute coupons on sunny days.

Interestingly enough, those that regularly go to bars and only occasionally (1-3 times) go to coffee shops seem to have a higher accepance rate than most at 59.5% and 55.1% respectively. 
This might make bars and coffee houses a good place to distribute or leave coupons.

Coupons that are good for a day are typically used much more than those which expire in a couple of hours.

Lastly, people that have their partner as passengers in their car are more likely to accept coupons than those with other passengers or no passengers (63.1% vs 42.1%).
This is another group that might be difficult to target but may be worthwhile to attempt to do so.

#### FYI:  The following are heavily, negatively correlated to coupon acceptance and should be avoided if easy to do so.
Snowy weather, below 30 temperature, late in the evening, within 2 hours of coupon expiration, to those who are retired, to those who are widowed, to those in the Installation Maintenance & Repair business or in the Farming Fishing & Forestry business.


#### Findings

It was decided to use the following criteria for filtering data:
    mid-priced restaurant attendace of at least 1x / month,
    the following occupations: Construction & Extraction, Healthcare Support, Office & Administrative Support, or Production
    the following times: 10AM, 2PM, or 6PM
    sunny weather,
    temperature above 30F, and
    coupons that expire in a day

By combining all of these criteria, we can get a high 85% acceptance rate.  However, this is only 20 of the 1492 total offers (1.3%).

By using any of these criteria, e.g. if we employed all targeting techniques, we would reach 1411 people of the 1492 coupon offers.  However, the 45.8% acceptance rate is only 1.7% greater than the 44.1% of the total sample population.  It could be that these coupons in the sample set already did a good job of reaching the subset of the population represented by the aforementioned criteria.  

Maybe what is most important isn't how many people we can reach with the coupons or the acceptance rate.  Maybe what is important is where to direct these coupon offers.


#### Next Steps

In the future we should look to see how much each of these criteria reduce the population size that accepts the coupons.
We could then use some logic to balance the number of offers and the acceptance rate.

It is also worth noting that the coupon distribution histogram indicates that the restaurant coupons were the least offered of all coupons.  This could indicate that this relatively small sample is not a good representation of the population as a whole.  We may want to get some more data.

