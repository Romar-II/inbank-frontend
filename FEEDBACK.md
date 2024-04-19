Biggest fix:
TASK 101 specifies that we need to display the highest amount according to chosen loan period.
In this case loan_form file compares for user chosen loan amount to the biggest available loan given by backend and displays the smaller amount.
This error is fixed

Smaller proposed fixes:
-Minimum displayed loan period on the slider is 6 months, should be 12, (fixed).

-Given its not binding calculator maybe its not that important but 
    there is an argument to be made to add some checks in the front end as well,
    something that makes sure that backend response is indeed between 2 000 and 10 000 euros, same thing with loan period.

-When landing on page loan amount and period is set to 2500 and 36 months, these seem to be chosen for aesthetics,
    which works for me, I would try to separate initial display variables from variables that we are actively checking information to improve readability

-Backend readability issues
    Would suggest to rewrite loan amount check and loan period check, in verifyInputs method, to avoid negations
    and put them in a separate method with proper names to improve code readability.
    For example:

    if (loanAmount>DecisionEngineConstants.MAXIMUM_LOAN_AMOUNT
    || loanAmount<DecisionEngineConstants.MINIMUM_LOAN_AMOUNT) {
    throw new InvalidLoanAmountException("Invalid loan amount!");
    }

    if (loanPeriod > DecisionEngineConstants.MAXIMUM_LOAN_PERIOD
    || loanPeriod < DecisionEngineConstants.MINIMUM_LOAN_PERIOD) {
    throw new InvalidLoanPeriodException("Invalid loan period!");
    }

TASK 102







Good: TRIES Frontend double checks backend response to be valid and accounts for backend response to be in some other form than in and makes it into int
in file loan form.dart