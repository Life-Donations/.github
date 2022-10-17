
**Title:** lifeDonations

**Description:** Your place to start a fundraiser or make an online donation for helping people, businesses, environment and other...

**Our Moto:**"No one has never become poor from giving"

**Main Features**

Login securely using our **extraordinary** implementation of JWT.

Install easily because of our **deployment** in Azure DevOps.

Scroll and change pages quickly with our app's **Single-Page Application** feature.

Enjoy while using and watching our platform because of **excellent design** and soft colors.

Donate or create fundraisers easily and make **our world** a better place.

Prove that you're not a robot by proving **your humanity**.

**About lifeDonations**

lifeDonations, Inc is a Albanian nonprofit website which was created in 2022 by Arbrore Halilaj, Dardan Prenaj, Jeton Sllamniku and Jusuf Hulaj. lifeDonatons, Inc is headquartered in Kosovo.

**Installation**

No need to install anything, just enter 51.138.44.16 on your browser search bar and that's it.

**Getting Started**

Go to the Sign In page by clicking the Sign In button which you can see on the top right of the page. To start using our website you should sign up first. Click on the "Sign Up" link and Sign Up page will be shown. Enter your credentials like the example below and click on the Submit button.

![Alt text](sign_up.png)

If you've already signed up, go to the Sign In page by clicking the Sign In button and enter your credentials. Click on the submit button. 
![Alt text](sign_in.png)

Now, to see current fundraisers click on the Fundraisers link which is located in the navigation bar. You will see a similar page like the one below. 
![Alt text](fundraisers.png)

If you want to donate to any of these fundraisers click on the View Fundraiser button. It redirects you to the donate page. Give the value you want to donate and write a message. Click on submit button. See the example below.
![Alt text]donate.png)

**Pages**

lifeDonations consist of these pages:

- **Sign Up Page**

Using Sign Up Page you are able to register your account after entering your information. Our Website is secured using JWT authentication method, which is one of the most secure implementation of authenticity in the industry.

On Sign Up page several inputs are shown. If the user fills each of those properly, he will be redirected to the welcome page where he can see his donations, of course none will be shown in the beginning since he just signed up. Otherwise if any of the fields is not filled properly the message will be displayed to inform the user what needs to be done.

This functionality is implemented doing a POST request from the front to the back of the application. When the request is sent a new user will be created in the database.

- **Sign In Page**

Using Sign In Page you will be able to enter your account if you have already Signed Up. If you haven't Signed Up yet, you can do so by clicking on the "Sign Up" and you'll be redirected to the Sign Up page.

After you enter the credentials, credentials will be checked and if both username and password are valid, you will be redirected to user page, where you can see your donations and fundraisers. Next time you visit our website, you don't need to re-sign-in because our websites uses the JWT token.

If credentials aren't correct you will be informed and won't be able to proceed unless what you entered is correct.

- **Home Page**

Home Page is the first page which is shown to users. Clicking on "Start A Fundraiser" sends you to "newFundraiser" page where you fill the form and if it's filled correctly, the fundraiser will start, meaning a new fundraiser is added to the fundraisers table in the database. In the bottom of Home Page are displayed the latest fundraisers, clicking on View Fundraiser button, you're redirected to the "/fundraiser" page, where you can see more information and are able to donate.

- **Fundraiser Page**

Fundraiser Page shows all the info about a fundraiser and has two buttons. Clicking on "Donate now" button you will be redirected to the donate page, where you can donate as much as you want and you can also give a message.

In Fundraiser Page you are able to see organizer of a specific fundraiser, category, date, type of fundraiser and the moneys raised till now.

- **Donate Page**

In this page an input for value to be donated and an input for the message are displayed as well as the submit button. You can't donate unless you enter some value greater than 0 and without writing a message.

When you click the Submit button, you are informed if donation was successful and you will be redirected to User Page.

- **Fundraisers Page**

In Fundraisers Page you can see the latest Fundraisers that are active. You are also able to View the fundraiser after clicking the respective button which redirects to the Fundraiser Page.

- **About Page**

In About Page you can see information about what is "lifeDonations", and history and more.

- **Contact Page**

In Contact Page after filling the form, you can contact our Team. An email will come to us with the message that you've entered.

- **Search Page**

When user clicks on the Search bar, he will be redirected to Search Page, where an input is displayed. As the user starts typing for what he wants to search, fundraisers will be filtered and only those fundraisers whose title contains what user typed in the input, will be displayed on the page. If no fundraiser exists for that search user will be informed.

**Documentation of Code**

Code was written in C# using ASP .NET web API.

The database is in Cloud, hence we can use the same data from different places.

Entity Framework was used to manipulate with data and connect with the database.

**The models used in the project:**

- Donation
- User
- Fundraiser

**The controllers used in the project:**

- UserController
- UserRegistrationController
- DonationController
- FundraiserController

**UserController methods:**

- **GetUser method** - works using http GET method and returns the first and last name of the user by id if it exists in the database, otherwise returns that the user wasn't found.
- **GetUserFundraisers method** – gets all the fundraisers of a specific user if there is any, if not NotFound() is returned.
- **GetUserDonations method** – is the same as the GetUserFundraisers method except that it gets donations of a specific user instead of fundraisers.

**UserRegistrationController methods:**

- **Register method –** this method is called when a user signs up. If the form is valid this method will check if any user with that email exists, if no user with that email doesn't exist a new user will be added to the database meaning that the user has registered successfully.

Also, a token will be generated and it will be returned to the user, who doesn't need to login on the subsequent requests because of the usage of JWT token.

- **Login method –** this method is called when a user tries to log in. If the username entered by the user doesn't exist, he will be informed that it doesn't and can't proceed unless he either enters the correct username or signs up first. Otherwise, if the username exists and the password entered is correct user will be able to proceed to our website. Also, when credentials are correct the token which is used in the subsequent requests will be returned.
- **GenerateJWT method –** is the method which generates a JWT token for each user. This method uses Identity methods such as SecurityTokenDescriptor and JWTSecurityTokenHandler to accomplish its functionality.

**FundraiserController methods:**

- **Get method** - returns all fundraisers that exist in the database.
- **GetLatest method** – returns the fundraisers which have started within the last 7 days.
- **GetFundraiser method** - works using http Get method and returns the specific fundraiser by id if it exists in the database, otherwise returns that fundraiser wasn't found.
- **SearchFundraiser method** – has three cases. The first case is when searching by title, in this case the fundraisers whose title contains the search string entered will be returned, if no such fundraiser exists the user will be informed. In the second case when searching by the category, fundraisers whose category contains the search string will be returned. In the third case when searching by type, the fundraisers whose type is the same as the type entered will be returned.
- **GetDonations method** – gets the id of a specific fundraiser, then returns all the donations for that fundraiser if these exist. Else, "No donations yet!" will be returned.
- **Create method** - adds a new fundraiser to the database using the http POST method.
- **Update method** – find a fundraiser by id and if it exists changes the database to reflect changes.
- **UpdateValue method** – updates the total value raised of a specific fundraiser, this method is called when a donation happens.
- **Delete method** - deletes a specific fundraiser if it exists, otherwise informs that the user isn't found.

**DonationController**

- **Get Method** - returns all donations that exist in the database.
- **GetDonation method** - gets a donation by id if it exists in the database, otherwise returns that the user wasn't found.
- **Create method** - adds a new fundraiser to the database using the http POST method.
