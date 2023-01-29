# Test Engineer technical assessment

## How this works

Thank you for your interest in a Test Engineer position with Heuristic Solutions! (*If you haven't already had a screening call with us, please do that first!*) 

This assessment will generate a code sample that we can collaboratively review in a technical interview. If you already have samples of your UI tests that you can share with us, those are acceptable too!

As part of the assessment, you will write a few tests against a simple, web-based sample application.

**There are two ways to take the assessment**:
1. We can give you a fully-provisioned virtual machine with the sample app and dev tools pre-installed;
1. You can install the sample app on your own machine and use the dev tools you already have installed.

It doesn't matter to us, we just want you to focus on writing the tests and not fighting with app setup headaches. 

## Using the virtual machine

At your request we'll send you a virtual machine image that already has the sample application installed, as well as Visual Studio, Selenium, nUnit, etc. All you need to do is log in and start writing tests!

You will need to download [VMWare Workstation Player](https://customerconnect.vmware.com/en/downloads/info/slug/desktop_end_user_computing/vmware_workstation_player/16_0) to access the VM. It is freely available.

You will also need about 60GB of free space to download the VM image from us.

## Running the sample app yourself

If you already have a .NET dev environment set up and don't want to download a huge VM image, that's great!

The sample app we're using is [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb). Clone that repo and follow the setup instructions in their README.

# Writing the tests

If you are using the virtual machine then we've already established a test project for you, and you will find the eShopOnWeb app at **https://localhost:5001**.

If you are not using the VM, then please create a **C# nUnit project with Selenium WebDriver**  to write your tests. You may need to adjust the instructions below to match your environment. 

## Test 1 - New users can register
**User story**: As a new user, I can register an account with the system so that I can log in to place orders using my saved information.

**Repro steps:**
1. Go to https://localhost:5001
1. Click the "Login" element in the upper-right part of the page
1. Click "register as a new user"
1. Enter an email address and a password, then click "register". (Password must contain at least one number and one non-alphanumeric character)

**Test conditions:**
1. After registering, the "Login" element in the upper-right corner is replaced with the email address of the logged-in user

![Login Flow](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/SampleApp-Login.png?raw=true)


## Test 2 - Users can search for products by brand
**User story**: As a user that is trying to find products for a specific brand, I can filter the product listing by that brand.

**Repro steps:**
1. Go to https://localhost:5001
1. Use the Brand drop-down to select a brand
1. Click the green ">" arrow to submit the search

**Test conditions:**
1. When using a brand that DOES have products associated with it, the list is correctly filtered to those products
1. When using a brand that DOES NOT have products associated with it, the user sees a "THERE ARE NO RESULTS THAT MATCH YOUR SEARCH" method

![Login Flow](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/SampleApp-BrandFilter.png?raw=true)


## Test 3 - Users can add products to a cart
**User story**: As a user that has added something to my cart, I can change the quantity that I wish to order.

**Repro steps:**
1. Go to https://localhost:5001
1. Add a product to your cart
1. Change the quantity of that item in the cart

**Test conditions:**
1. The order subtotal is correctly updated

![Login Flow](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/SampleApp-ShoppingCart.png?raw=true)


## Test 4 - Users can place orders
**User story**: As a user that has added something to my cart, I can submit the order to complete the checkout process

**Repro steps:**
1. Go to https://localhost:5001
1. Add a product to your cart
1. Click "checkout"
1. Confirm order details and click "Place Order"

**Test conditions:**
1. User sees a "Thanks for your Order" confirmation page
1. User can view the order details by going to their "Order History" page

![Login Flow](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/SampleApp-OrderDetails.png?raw=true)


## Test 5 - Admins can create new products
**User story**: As an administrative user, I can add new products to the system so that they are available to purchase.

**Repro steps:**
1. Go to https://localhost:5001/admin
1. Log in as "admin@microsoft.com" with password "Pass@word1"
1. Click the blue "Create New" button and fill out the form

**Test conditions:**
1. When fields are left blank, user sees validation messages about required fields being left blank (Name, Description, and Price are required)
1. Newly-added products appear in the list

![Login Flow](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/SampleApp-AddProduct.png?raw=true)


## Test 6 - Admins can delete existing products
**User story**: As an administrative user, I can delete products we no longer offer so that they cannot be purchased any longer.

**Repro steps:**
1. Go to https://localhost:5001/admin
1. Log in as "admin@microsoft.com" with password "Pass@word1"
1. Click the red "delete" button to delete an existing product
1. Confirm the details in the modal popup, then click "Delete" again

**Test conditions:**
1. Deleted items no longer show up in the list
1. Products can be deleted even if orders exist that reference them
1. Users can access historical Order Details pages for products that have been deleted
1. Deleted products DO NOT show up in the front-end product list and cannot be purchased any longer

![Login Flow](https://github.com/HeuristicSolutions/Heuristics.TestEngineerEval/blob/main/assets/SampleApp-DeleteProduct.png?raw=true)

# What's next?
When you're finished, you can send us a link to your GitHub repo, or you can zip up your test project and email it. 

(If you want to email it, please upload to your Google Drive or OneDrive or something and send us a link to it; our email system sometimes rejects .zip attachments)

After we've received and reviewed your code we'll send you an invite for a core review interview where we'll talk about how you approached the problems, ask questions about other ways you could have done it, etc.

**Want to earn "extra credit"?** Be prepared to talk about:
1. How you might handle repeated logic
1. How you keep your tests from being brittle and slow
1. How do you decide what should be tested via the UI, and what shouldn't? Are there examples from this assessment that you think should have been tested another way?
