# (Loan Dataset Exploration)
## by (Saud BinGhushayan)


## Dataset

> The dataset that I'm going to explore is loan dataset which contains 81 columns and 113937 observations , ofcorse I'm not going to need all the 81 columns so I did some wrangling efforts to clean Quality and tidiness Issues and also to drop the unnecessary columns , after cleaning the data I selected only 16 columns that I found interesting and might help me with my analysis and visualization , my main focus is to look at the nature of loans and what most loans for , does high amount of loans have high amount of monthly payment , the APR associated with loan status and finally the reason that loans are defaulted . I also looked at the top 10 loan categories with different aspects like whats the most loan that are defaulted and why it's defaulted .

## Summary of Findings

> I found that the most loans are for `Debt Consolidation` with 62.2% and the second most picked loan is 10.8% you can imagine the difference , nearly all loans in this dataset are for `Debt Consolidation`  , and we have very little defaulted loan and it is because of the high APR and most loans with low amount and low monthly payments are defaulted , high APR are associated with low loan amount and low monthly payments and that's why the loans are defaulted , the higher the loan amount the higher the monthly payments will be yet as shown in the plots there are loans with high amount and low monthly payments I think these columns are Long-term loans , after selecting the top 10 listing categories of the loan I found that nearly all loans are defaulted because of the high APR except for the wedding loans which makes it interesting . 


## Key Insights for Presentation

> In the presentation I introduced the data that I'm going to explore and what cleaning parts will I do , after that I focused on introducing the exploration for the interested variables in the dataset , first introducting the Univariate exploration showing BorroweAPR distribution and ListingCategory countplot , after that moving to the Bivariate exploration showing the relation between APR and loan status , and the relation between loan amount and monthly payments , Finally I'll introduce the Multivariate analysis and the relation between the loan amount and monthly payment for the top 10 listing categories , I'll show also the relation between APR and loan status for the top 10 listing categories . 