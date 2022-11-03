---
layout: post
title: Hosting your Website on GitHub Pages Using a Custom Domain
permalink: /githubpages_custom_domain/
---

I've designed this website using this template [Jekyll Now](https://jekyllnow.com) and it's hosted on GitHub pages. But if you're like me you probably want your URL to be custom and not use what github gives you (with the github.io extension). I'm assuming that you already have a domain name purchased from sites like GoogleDomains, GoDaddy.com etc. I purchased mine through Google Domains.

The first thing to make sure, even before worrying about the domain, is whether your site is actually deployed on GitHub Pages properly. If not, redirecting your site from pages to your custom URL won't be possible. 

Go to Settings, Click on the Pages tab on the left hand side and check if it says "Your Site is Live at https://example.github.io". If not, make sure it is being built from the correct branch. For example, mine is using the master branch and the root directory. 

But if you're all set till here, the next step is where we set the custom domain. On the same page, you will see a custom domain section. Type in the domain name you've purchased (achyutganti.com in my case) and hit save. Somewhere on the top of the screen, you should see a pop up saying A Custom Domain has been added. But you would also see that warning message in orange or red saying "The domain name or the alternate name have not been configured". Don't worry. Check "Enforce HTTPS" under that if not already. 

Go back to your respository where the source code is stored. You will notice that GitHub has created a new file under the name CNAME. You will see the domain name if you click on it and nothing else. 

At this stage, we've taken care of everything we need to on the GitHub side. Before we go to Google Domains, click on [this link](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site). Scroll down until you reach the "Configuring the Apex Domain section". Under that we need those 4 IP addresses at point #5. These are important for our A record. 

Now go to Google Domains and log in with your credentials. Go to My Domains tab on the left hand side and you should see the domain you've purchased. Click on it. Again, on the left hand side, you will see the DNS section. Clicking on it will take you to a page which says Default Name Servers and Custom Name Servers. Under the Default Name Servers section you should see a custom records section. We will add two types of records here. There are four fields here, Host name, Type, TTL and Data. 

For the first record, Select Type as "A" and add the 4 IP addresses as separate rows. For the second record, enter "www" for Hostname, "CNAME" for Type and "example.github.io" for the Data field and Hit save.

You should see this message "These DNS settings are active. Changes are published immediately, but may take time to propagate" on the top in green. GoogleDomain says that it takes nearly 48 hours for those changes to reflect but it is much faster than that in reality. 

