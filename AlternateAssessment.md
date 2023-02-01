# Test Engineer technical assessment

| :exclamation:        | Only use this assessment if we directed you to it. Most people should use the instructions in the main README file instead. |
|---------------|:------------------------|

## How this works

Thank you for your interest in a Test Engineer position with Heuristic Solutions! (*If you haven't already had a screening call with us, please do that first!*) 

The purpose of this assessment is to create a code sample that we can collaboratively review in a technical interview. If you already have samples of your UI tests that you can share with us, those are acceptable too!

To keep things simple, you will write some UI tests against our publicly-accessible training instance so that you don't need to worry about installing anything locally (except your testing framework of choice).

## Setting up the system under test

Since we serve the licensing and credentialing industry, we have created a fictional licensing organization called the "American Society of Office Dogs" to serve as a sample scenario :) 

You will be writing tests against our QA training site: [https://training.qa.learningbuilder.net/](https://training.qa.learningbuilder.net/)

**Note:** We turn off our QA sites when they are not being used, so you may need to click a button to start it up:

![Starting the test site](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/TurnSiteOn.png?raw=true)
 
**It may take a few minutes to fully start up, and pages may be slow to load the first time you access them.** The training site is hosted on a shared server with other QA resources; if responsiveness becomes an issue for you, please reach out and let us know!

## How to log in

The training site has a number of pre-created accounts. To make it easy, they are listed on the login page, and you can click on a name to log in as that persona.

![Logging in](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/HowToLogIn.png?raw=true)

# Writing the tests

You are welcome to write your UI tests using whatever tool you would like. 

We use Selenium, C#, and NUnit but you can use what's familiar; the point is to figure out how you think about automated testing, not to trip you up with platform-specific trick questions.

Using your tool of choice, please write the following tests: 

## TEST 1 - New user can successfully create an account

**User story:**
"As an aspiring Office Dog, I can register a new account with the system so that I can begin my licensing journey."

**Repro steps:**
1. Click the orange "Get Started" button in the upper-left part of the login page
2. Fill out the registration form and submit it

**Test requirements:**
The test is considered successful if the user is redirected to the "Email Confirmation" page:
![Email Confirmation Page](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/EmailConfirmationPage.png?raw=true)


## TEST 2 - Users are prevented from submitting duplicate email addresses

**User story:**
"As a user that is trying to register a new account with an email address that already exists, I am notified that the email address is in use and I am prompted to perform the Forgot Password flow instead"

**Repro steps:**
1. Click the orange "Get Started" button in the upper-left part of the login page
2. Fill out the registration form, using an email address that is already in use (e.g. listed on the login page)

**Test requirements:**
The test is considered successful if the user sees an alert message containing a link to the Forgot Password page:
![Already Exists Popup](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/EmailExistsPopup.png?raw=true)


## TEST 3 - Admin users can search for other users by Role and Status

**User story:**
"As an administrator user, I can search for Members by Role and Status so that I can easily find accounts in various busines states."

**Repro steps:**
1. On the login page, click on "Arlene Admin" to log in as an administrator
2. In the main nav bar, click on *Admin -> Members*
3. In the "Role" dropdown, select "Office Dog"
4. In the "Status" dropdown, select "Applicant"
5. Click "Filter"

**Test requirements**
The test should assert that:
1. "Barky McBarksALot" is included in the search results
2. The filter criteria (Role and Status) retain their values after the results are shown

![Admin Search Results](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/AdminMemberSearch.png?raw=true)

## Submitting your code sample

You can send us a link to your GitHub repo, submit a PR to this one, or email us a .zip file; whatever works for you works for us.

Want to earn "extra credit"? Be prepared to talk about:
* How you might handle repeated logic, such as logging in
* How you keep your tests from being brittle and constantly breaking when minor code changes are pushed
* How you manage test data, such as knowing that "Barky McBarksALot" should already exist in Test 3