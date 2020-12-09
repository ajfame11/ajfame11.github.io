---
layout: post
title:      "Utilizing OmniAuth"
date:       2020-12-09 02:05:19 +0000
permalink:  utilizing_omniauth
---


I created a new project, difference being that this was my first time using ruby on rails to create a project. A feature for the project was to utilize OmniAuth and allow users to connect their account on my application to Github. It was a difficult process at first when learning how to do this, but over time it became easier to understand and implement into my project. Though it worked, I did find that they were one too many steps when using OmniAuth for my project. So I want to attempt at writing out a step by step process of how to utilize OmniAuth for ruby on rails.

Step 1: You need to add the gem to your Rails app Gemfile. There are multiple gems for OmniAuth but the gem I used is called  ‘omniauth-github’

![](https://lh3.googleusercontent.com/gmxdsfjyAIC0Fhf09dKvKwSoRST5XZIy_Z4bn7b0sg2nwW2NOZtSHS22c30F7vpPOSQR=s170)

Step 2: Set up your OmniAuth configuration. In config/initializers, create a file called omniauth.rb.

![](https://lh3.googleusercontent.com/ukm6I3O6BAfBGpBIwU3ETYftnFcJ8EWN9G0khsFeHs7tuL6440EXjXSRM6yvekWDCQPz=s170)

At this point, the application knows that Github is the provider, and that it needs to reference a specific Github Client Key and Github Secret Key. To get these 2 important credentials, you’ll need to register your app onto Github. The process for that is as followed:

1. Sign in to Github, then in the top right corner of the page, click on your profile picture and select Settings. From there, click on Developer Settings, then New GitHub App.

![](https://lh3.googleusercontent.com/-fwd0GVgHpGffw19UnuPapSN3Z27yx-wp0cfdwafG1K7eWofFUAERCQdORSQrv42o2GsFg=s170)

2. Fill out the form with your Application name and Homepage URL.

3. Complete the Authorization callback URL. We’re going to set this up as /auth/github/callback.

![](https://lh3.googleusercontent.com/x19DpYZhzt94SH9MNAixIk13QoVKO7vnpHp3fOEg0WwKLn_K6ZFrvljL2r6vWekJ_qh25A=s170)

4. Once you’ve registered your application, you’ll be taken to a page that displays your Client ID and your Client Secret. Then you’ll need to input these into your Rails app. These keys should never be hard-coded  into the application! I learned the hard way that that’s a good way to get your keys revoked real quick!

5. One way I learned to avoid this mistake is to use a gem called ‘dotenv-rails’ to keep everything kosher with our Github keys. In your Gemfile add gem ‘dotenv-rails’ and run bundle.

6. In the Rails app, you’ll notice that a new, grayed-out file called .env has been created.

![](https://lh3.googleusercontent.com/CHt_AebZYK0xbaC06OqumNA6rYZ0mTwglzLs3AgCKIy9QgiJnGIoSrX_TWjlwiGrBowvzw=s85)

7. From there simply add the keys in the file as such format.

![](https://lh3.googleusercontent.com/0K1HxRXnlJK_HId2KHMH1uMetfe3ufOSkj3OvVaN9FQC_PsBEiPRXylgiq44fcI_8icg1Q=s170)

8. Now the omniauth.rb file knows what ENV[‘GITHUB_CLIENT_ID’] and ENV[‘GITHUB_CLIENT_SECRET’] means without risking that your credentials will be revoked and now back to the original steps!


Step 3: Add a link in your view for users to access this new authentication. Here is my example:

![](https://lh3.googleusercontent.com/jeRo_rT74uWhmP89fP4fz4R6hSFsBRPBYzYe2DjyXBZYdM75E8cMg4e_fMkQrjebWwz1cA=s170)

Step 4: Add your login path and callback url to your routes.

![](https://lh3.googleusercontent.com/-MIWJkYTZZbLjByHVySwXB6MMDURZZbGQ231lkUQ34vxXzzLawOBtLqVemMYu8NvuvjWFxY=s170)

Step 5: We finally get to call OmniAuth! To better your understanding of all of the foundations of Rails OmniAuth would mean to go back to the beginning as a great way to help clear up the confusion of tools like this and to also put in practice, plenty of practice. As the saying goes, practice makes perfect!


