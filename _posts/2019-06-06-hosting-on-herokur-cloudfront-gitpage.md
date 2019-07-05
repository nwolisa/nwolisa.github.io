---
layout: post
title: "Hosting a static website using Heroku, Cloudfront and Github Page"
date: 2019-06-06
---

There are times when you want to kick up a simple website without necessarily using the regular hosting offered by Hosting companies or spinning up a server on one of the cloud providers. 

Hosting a static website using S3 bucket is already well documented. If you have the domain registered on AWS Route53 then even better because you can use Route53 alias for AName to ensure your root domain and any subdomain, like www, all point to the same resources. 

http://example.com -> Homepage
http://www.example.com -> Homepage

Below I will describe the steps to create a static website using Node/Express and host it on Heroku add a custom domain on Heroku and use S3 static hosting to redirect the root domain to the custom domain (subdomain) pointing at the Heroku app.

Create a GitHub repository
	Clone the application to your local machine

Create an ExpressJS application
	>`$ express examplesite --git -e`

Create an app on Heroku
	* Go to the deploy and tab and choose Github as your deployment method
	* Choose the repository you want to deploy
	* Choose the branch (default master) you want to deploy

Push your changes to GitHub
	This will trigger an auto build on Heroku
	Use heroku cli tool and the command below to view the logs:
		>`$ heroku logs --tail --app examplesite`

Register a domain on Route53

Go to the setting tab in Heroku
	* Click on Add Domain 
	* Or use the command below:
	>`$ heroku domains:add www.examplesite.com --app examplesite`

View your added domain and the Heroku DNS target

Go to the Route53 dashboard and add the CName record to the domain
	Create Record Set
	Name: www.examplesite.com
	Type: CName
	Value: Heroku DNS target
	Alias: No


> https://nimaeskandary.com/2018/02/11/setting-up-a-blog.html