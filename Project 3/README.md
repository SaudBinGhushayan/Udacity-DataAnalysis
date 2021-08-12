### Project Describtion 
-----------------------------
In this Project we are comming to decide whether the company `e-commerce` should launch the new web page or not

__Dataset shape__
----------------------------
This dataset has `294478` rows and `5` columns 

__Cleaning The Dataset__
--------------------------
This dataset has some wrong values which I cleaned 

The wrong values are that the `landing_page` for the `control` group must be with the value of `old_page`

and the `landing_page` for the `treatment` group must be `new_page`

__After performing the A/B testing I came with this:__
--------------
After performing A/B testing I came with the result of `p-value is = 0.9` and this value provides us with the information on whether to reject the null or fail to reject the null .
if the p value was greater than the type I error we come with the decision to Fail To Reject The Null which exactly our case but if the p value was less than type I error we can say that the the value is statistical significance and we Reject The Null
We can stop testing after bootstrapping for 10000 iterations and come with a final result after that.

__Glossary:__
with the above calculations we come with that our old page is better than the new page
with a high number of tests we can come with the right conclusion

__After fitting Logistic Regression Model__:
-------------
Interpreting The Results Of The Model :
1. if an individual recieved control he's 1.015 times more likely to convert than if he recieved treatment.
2. since the p_value of the ab_page is 0.1897 not equal to 0 we come to Fail To Reject The Null . 

__After fitting Logistic Regression Model with the interaction between page and country__:
-------------
1. First we concluded that the countries columns didn't make any difference with the conversion of individual.
2. looks like our new countries columns ins't significance since the p value assosiated with them doesn't equal to 0 we come to Fail To Reject The Null.

__Conclusion__
--------------------------------------
After calculating the probabilities , performing A/B tests and performing Regression tests we come with the conclusion that the company __"e-commerce"__ 
should not implement the new page and just stick with the old page 
