I've designed this website using this template [Jekyll Now](https://jekyllnow.com) and it's hosted using GitHub pages. But if you're like me you probably want your URL to be custom and not use what github gives you (with the github.io extension). I'm assuming that you already have a domain name purchased from sites like GoogleDomains, GoDaddy.com etc. I purchased mine through Google Domains.

The first thing to make sure, even before worrying about the domain, is whether your site is actually deployed on GitHub Pages properly. If not, redirecting your site from pages to your custom URL won't be possible. 

Go to Settings, Click on the Pages tab on the left hand side and check if it says "Your Site is Live at https://example.github.io". If not, make sure it is being built from the correct branch. For example, mine is using the master branch and the root directory. 

But if you're all set till here, the next step is where we set the custom domain. On the same page, you will see a custom domain section. Type in the domain name you've purchased (achyutganti.com in my case) and hit save. Somewhere on the top of the screen, you should see a pop up saying A Custom Domain has been added. But you would also see that warning message in orange or red saying "The domain name or the alternate name have not been configured". Don't worry. 

Go back to your respository where the source code is stored. You will notice that GitHub has created a new file under the name CNAME. You will see the domain name if you click on it and nothing else. 

At this stage, we've taken care of everything we need to on the GitHub side.