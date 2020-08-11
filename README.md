Predicting Home Credit Loan Default

Introduction:

Credit defaults pose a major threat to the profitability of banks and other lending
institutions. The problem of bad loans has taken gigantic proportions in India and all
over the world. In the past few years,we have seen a few high-profile cases of defaults
worth thousands of crores, and innumerable instances of medium to minor level loan
defaults. Non-performing loans have the potential to impact the GDP of a nation. Hence,
it’s imperative to find a robust method of credit appraisal, to improve the overall health
of the credit portfolio.

Problem Statement:

The current credit appraisal process includes analysing past credit history and taking
decisions based on the Credit Rating provided by external rating agencies to borrowers
(for example, CIBIL score in India). Though this method is somewhat effective, it has
many loopholes. We cannot be cent per cent sure about the future, based on just the
past records of a borrower’s repayment habits. A borrower with a good past record may
default, and another with a shady record, may turn out to be a diligent loanee. Hence,
we need to build a more detailed and robust appraisal system that takes the general
credit health scenario into account in addition to the specific attributes of the customer,
and predicts a probability of default, based on mathematical modelling. This helps
extend credit only to deserving customers, and weed out shady clients.

Broad Methodology for EDA and modelling:

1. Cleaning and preprocessing - data provided to us maybe in incorrect format,
containing garbage values, missing values, or in some other unusable form.
Machine Learning models cannot work with data in this form. Hence, we need to
preprocess the data and “clean” it to bring it into the desired form for modelling
2. Carrying out visual EDA for getting a general sense of data and understanding
the relationships between various attributes- the dataset has a large number of
columns. A careful and in-depth study of the distribution of the features can
provide hidden trends in customer behaviour. In addition to aiding us in
developing a model, uncovering such trends can help credit appraisal teams look
for specific traits in customers, or discard other traits.
3. Ascertaining critical attributes and their effect on target - being given a large
number of attributes may be good or a bad thing. Proper utilization of all features
to improve modelling accuracy, can result in better results. On the other hand,
incorporating unimportant and insignificant features into our model can make our
model more complex than is optimally required, and decrease predictive
accuracy
4. Applying ML models to predict default probability - the final aim of this capstone
is to develop a model to predict probability of default. Though we are not
classifying a customer as “good” or “bad” directly, this is a classification problem
because we are given the training data target as binary values of 0 and 1 and we
have to train a classifier using this data. At the first look, it seems that
LogisticRegression with optimal hyperparameters may suffice for the task, as it
can output probabilities and is good for binary classification. As the modelling
progresses, we will try out other models, taking into account various
combinations of features (dropping or keeping features) based on significance
tests.

Brief description of the dataset:

- The main data is present in the file “application_train.csv”. There are many
auxiliary files that contain details about the customers credit card balances,
previous inquiries for credit, credit rating bureau data, etc. The primary dataset is
the one with the core features of the customers, and containing the TARGET
values, representing whether it was a “good” or “bad” loan. This dataset will be
used for our modelling, as the attributes present in this dataset contain rich and
varied information about a customer’s demographics and personal history.
- Each loan has been given a unique ID, called the SK_ID_CURR, that represents
the application ID of the current loan of the customer in the Home Credit
database. This field is insignificant for modelling, and hence will be used only to
analyse trends in exploratory data analysis.
- WIth common sense and domain knowledge, it is evident that some attributes
may turn out to be more important than others in modelling. For example, the
default probability may be heavily influenced by the customer’s income. The loan
amount of the customer may be dependent on the income. We may observe
more defaults by unemployed people. People working in a particular type of
industry may be better overall borrowers. The social circle of the borrower may
affect his/her repayment habits. A particular type of loan may be getting paid
better than others. More educated people may be less prone to inconsistent
repayment habits. As we carry out EDA, we will be able to find out the truth about
these assumptions.
- There are 123 columns in the main dataset, comprising categorical and numeric
features. The pandas types allocated to the features are “int64”, “float64” and
“object”. But we need to apply appropriate conversions, depending on the
feature’s meaning.
- Features like client’s income, credit amount, etc are numeric, and no
preprocessing is required for them as they have been identified correctly by
pandas. Null values in these columns are replaced with either a central
statistic(mean/median/mode), or 0, depending on the significance of the feature
on the TARGET. The detailed process for handling null values has been
described below.
- Some columns are stored as type ‘object’, but in reality, they are categorical. The
values in these fields are in the correct format, and no string preprocessing is
required as these will be converted to categorical type for modelling. Null values
will be handled based on the importance of the feature on the TARGET, as
described below.
- Some fields contain negative as well as positive values, for example,
DAYS_ID_PUBLISH. This field represents the days passed since the client got
their ID changed. Negative and positive values will be analysed coherence and
consistency with the real world. They will be handled accordingly.
